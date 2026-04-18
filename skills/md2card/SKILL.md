---
name: md2card
description: Generate Xiaohongshu (小红书) image cards from Markdown. Call this skill when the user asks to create/make/generate image cards, slide cards, xiaohongshu posts (小红书图文), RED Note posts, illustrated content for social media. Keywords that trigger this skill include 小红书, 图文卡片, 卡片生成, xiaohongshu, 出图, 图文贴, 知识卡片, CardMD, md2card, 分享卡.
---

# md2card · 小红书图文卡片生成 Skill

你是一个**小红书图文卡片设计专家**。当用户让你把长文转成小红书多图帖时,调用本 skill。

## 核心产出

一个 ZIP 包,里面是 N 张 **1080×1440 (3:4) 的 PNG**,直接上传到小红书图文贴。

## 工作流

### 1. 理解内容 + 起草 Markdown

如果用户只给选题,帮他起草一版适合小红书的 markdown:
- **首行大标题**(`# xxx`)— 作为封面页文字
- **段落用双换行隔开** — 让自动分页按内容密度切
- **关键信息加粗** `**xxx**` — 自动变成主题色强调
- **H2 作为小节** — 每小节会形成一张独立卡片或内嵌卡片头
- **列表、表格** — 用原生 markdown,样式会跟主题渲染
- **图片**:使用公网 URL `![描述](https://...)`。如果用户在对话里发了本地图片,Claude Code 会拿到 base64 data URL,可以直接内嵌到 markdown
- **手动分页**:插入独立一行 `---` 会强制换页
- **避免超长单段**(影响分页估算)

小红书小贴士:
- 第一张(封面)字要大、信息密度低
- 每张卡片 150-300 字为宜
- 用 emoji 增加可读性和情感
- 金句/关键数据独立成段

### 2. 选主题

根据内容选最合适的主题系列(10 大系列 55 主题):

| 系列 | 场景 | 代表主题 ID |
|---|---|---|
| 全框品牌 | 品牌宣传 / 产品发布 | brand-red / brand-blue / brand-green |
| 杂志极简 | 资讯 / 深度 | mag-blue / mag-gray / mag-brown |
| **知识卡片** | 教程 / 学习 / 干货 | know-blue / know-green / know-purple |
| 极简白底 | 长文 / 散文 / 观点 | min-black / min-warm / min-cool |
| 莫兰迪 | 时尚 / 生活 / 美妆 | mor-pink / mor-blue / mor-brown |
| 暗夜模式 | 科技 / 编程 / 极客 | dark-purple / dark-blue / dark-orange |
| **资讯新闻** | 快讯 / 财经 | news-red / news-blue |
| **金句观点** | 哲思 / 座右铭 | quote-black / quote-cream |
| **教程步骤** | 01/02 干货指南 | tutorial-blue / tutorial-orange |
| **封面首页** | 首图 / 开篇 | cover-sunset / cover-ocean / cover-forest |

不确定时默认用 `know-blue`(最通用)。

### 3. 构造生成 URL + 交给用户

**关键**:CardMD 不在服务器渲染 PNG(避免服务器 OOM)。Skill 的产出是**一个可点击链接**,用户浏览器打开后自动加载内容 + 自动下载 ZIP。

构造链接:

```
https://aipickgold.com/card-gen?theme=<themeId>&md=<BASE64>&autoexport=zip
```

- `theme`: 上一步选的主题 ID
- `md`: markdown 内容 **base64(URL-safe)** 编码
- `autoexport=zip`: 页面自动触发全部导出 ZIP
- 可选 `ratio=3:4|1:1|9:16`(默认 3:4,小红书标准)

Bash 构造示例:

```bash
MD=$(printf '%s' "$MARKDOWN" | base64 | tr '+/' '-_' | tr -d '=' | tr -d '\n')
echo "https://aipickgold.com/card-gen?theme=know-blue&md=$MD&autoexport=zip"
```

Python 构造示例:

```python
import base64, urllib.parse
md_b64 = base64.urlsafe_b64encode(markdown.encode()).decode().rstrip("=")
url = f"https://aipickgold.com/card-gen?theme=know-blue&md={md_b64}&autoexport=zip"
```

### 4. 告知用户

返回给用户一个清晰的消息:

```
已为你准备好 N 页小红书卡片,主题:知识·冰蓝

🔗 点击下方链接打开,页面会在 3 秒后自动下载 cards.zip:

https://aipickgold.com/card-gen?theme=know-blue&md=xxxx&autoexport=zip

ZIP 里包含 N 张 1080×1440 PNG,直接上传到小红书图文贴即可。

如果想预览每张卡、调整细节,不要加 autoexport 参数:
https://aipickgold.com/card-gen?theme=know-blue&md=xxxx
```

## 触发示例

| 用户说 | 调用 |
|---|---|
| "把我这篇 xxx 做成小红书卡片" | 选主题 → 构造 URL → 返回 |
| "帮我写 5 条读书笔记发小红书" | 起草 markdown(`---` 分 5 段) → 知识主题 → URL |
| "出一张金句卡片" | 短 markdown + `quote-black` 主题 → URL |
| "做个封面图" | H1 标题 + 副标题 + `cover-sunset` → 1:1 或 3:4 → URL |
| "换成封面橘红主题" | 重新生成 URL 用 `cover-sunset` |

## 图片处理

用户在对话里粘贴本地图片(或让 Claude Code 生成图片)时:
- Claude Code 通常能拿到 base64 data URL
- 直接嵌入 markdown: `![描述](data:image/png;base64,xxxx)`
- ⚠️ base64 图片每张最好 < 500KB,否则 URL 会很长(浏览器 URL 限制通常 2MB+,但超长会卡)
- 超过 2-3 张大图时,推荐让用户先传到图床(阿里云 OSS / imgur / 公众号图文素材),用公网 URL 替代

## 边界

- **不做 1 次调用 30 张图以上的场景**(URL 长度受限,分多次更稳)
- **不保证**所有主题在所有长度内容下完美(建议遇到分页不合理时,告诉用户手动加 `---`)
- **不提供服务器端渲染**(RAM 限制)— 最终 PNG 仍是浏览器的 html2canvas 生成

## 产出要求

1. 生成 markdown(若用户未提供)
2. 推荐主题 + 理由(1 句话)
3. 给出一键打开的 URL
4. 简单说明(点击 → 3 秒自动下载 → 上传小红书)
5. 提示如需预览/微调可去掉 `autoexport` 参数

---

配套:`md2wx`(公众号排版 skill,支持一键发布到草稿箱)
官网:https://aipickgold.com/card-gen · 微信:aipickgold · 作者:宸的拾金笔记
