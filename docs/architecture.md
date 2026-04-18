# md2card · 架构说明

## 为什么不做服务器端图片生成

大多数"HTML 转图片"工具在服务器端跑 Puppeteer 或 headless Chrome,一张 1080×1440 PNG 消耗几百 MB 内存。我们的阿里云 ECS 实例只有 894MB,跑一个 Chrome 进程都会挤爆。

我们的选择:**所有图片渲染在用户浏览器完成**。服务器只托管静态资源。

## 架构

```
┌─────────────────────────────────────┐
│ Layer 1 · 用户侧                     │
│ ──────────────────                   │
│ 🧠 Claude Code Skill(首推)          │
│    - 在 AI 对话里触发                 │
│    - 构造 URL 返回给用户              │
│                                     │
│ 💻 网页(降级备选)                   │
│    aipickgold.com/card-gen          │
│    - 手动粘贴 markdown                │
└──────────────┬──────────────────────┘
               ↓ 打开 URL
┌──────────────┴──────────────────────┐
│ Layer 2 · 浏览器侧                    │
│ ──────────────────                   │
│ React + Tailwind                    │
│ ├─ 读 URL 参数(md / theme / zip)   │
│ ├─ card-engine.ts 自动分页 + 渲染    │
│ ├─ html2canvas 每页截图             │
│ ├─ JSZip 打包                        │
│ └─ 触发浏览器下载                    │
└──────────────┬──────────────────────┘
               ↓ 静态资源请求
┌──────────────┴──────────────────────┐
│ Layer 3 · 服务器(静态托管)          │
│ ──────────────────                   │
│ 阿里云 ECS + Nginx                   │
│ 只做 2 件事:                        │
│ 1. 托管 .html/.css/.js 静态资源     │
│ 2. 托管 /api/convert(可选 JSON 服务) │
│                                     │
│ 零图片生成、零 Chrome、零存储        │
└─────────────────────────────────────┘
```

## 为什么这么设计

### 1. 成本
阿里云 ECS 894MB RAM 月付约 ¥80。如果加 Chrome 渲染,起码得 4GB 实例,月付 ¥300+。客户端渲染保持低成本。

### 2. 隐私
- 你的 markdown 永远不经过我们的服务器持久化(只在 URL 参数里瞬时)
- 图片在你浏览器生成,直接从内存保存到硬盘
- 我们看不到任何中间产物

### 3. 速度
- 服务器响应 < 100ms(静态资源)
- 渲染时间取决于你的电脑(通常 2-5 秒 for 5 页)
- 如果用户电脑好,比服务器渲染还快

### 4. 可扩展
- 服务器几乎不承担计算,轻松扛 10 万日活
- 浏览器负载分布式,用户越多服务器负担没变

## 关键技术

### URL 参数编码

```
aipickgold.com/card-gen?
  theme=know-blue               ← 纯文本
  &md=IyDpmJTor4vnrJQ...        ← base64 URL-safe(+→-, /→_, 去 =)
  &autoexport=zip               ← 指令
```

Markdown 用 JavaScript 的 `encodeURIComponent(btoa(md))` 处理,服务器端 `atob` + `decodeURIComponent`。

### 字体加载

3 个开源字体(思源宋体、霞鹜文楷、得意黑)从 jsDelivr CDN 加载。首次访问会下载几 MB,之后缓存。导出前 `await document.fonts.ready` 确保字体就位。

### html2canvas 原理

1. 遍历 DOM → 计算每个元素的 computedStyle
2. 用 `<canvas>` 重新绘制
3. `canvas.toBlob("image/png")` 生成 PNG Blob

局限:
- 某些 CSS 特性(`backdrop-filter`、复杂 gradient)支持不佳
- data URL 图片完全支持,跨域 URL 图片需要服务器返回 CORS 头

### 分页算法

`card-engine.ts` 的 `splitPages()`:

1. 如果 markdown 包含 `---` 独立行 → 按 `---` 分页(手动优先)
2. 否则按段落估算字符数 → 每页塞满到 ~380 字 → 自动切

字号 / 行高变化时自动重算。

## 极端情况

### 图片太多 URL 太长

- 浏览器 URL 限制通常 2MB,base64 膨胀 1.33 倍
- 超过 10 张图 + 2000 字文本建议分多次生成
- 或者让 Skill 提示用户:先传图床拿公网 URL,再用 `![](https://...)` 引用

### Skill 构造的 URL 被浏览器拦截

- 部分浏览器(Safari 隐私模式)会拦截程序触发的下载
- 解法:用户手动点页面上的"全部导出"按钮

### 自定义主题

- 目前 55+ 内置主题已覆盖主流场景
- 未来路线:主题市场(社区贡献 → 审核 → 上架,贡献者署名)

## 服务器端扩展(可选)

如果未来要做"API 批量生成"给企业用户:

- 加一层 Cloudflare Workers 或 Vercel Edge Functions
- 用 `@vercel/og`(基于 Satori)在边缘节点做 SVG → PNG
- 不在我们的 ECS 上跑 Chrome

这是 Enterprise 档位才考虑的功能。

---

有建议?[Issue](https://github.com/aipickgold/md2card/issues)。
