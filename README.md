# md2card · 小红书图文卡片生成器

<div align="center">

<br/>

**一键把长文切成精致的 3:4 小红书图文卡片**

**55+ 主题 × 10 大系列 · Stitch 风高级工作区 · 发稿只花 30 秒**

<br/>

[![Website](https://img.shields.io/badge/官网-aipickgold.com-F43F5E?style=for-the-badge&logo=webpack&logoColor=white)](https://aipickgold.com/card-gen)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](./LICENSE)
[![Themes](https://img.shields.io/badge/Themes-55%2B-F43F5E?style=for-the-badge)](https://aipickgold.com/card-gen/themes)
[![Stars](https://img.shields.io/github/stars/aipickgold/md2card?style=for-the-badge&logo=github&color=yellow)](https://github.com/aipickgold/md2card/stargazers)

<br/>

[官网使用](https://aipickgold.com/card-gen) · [主题画廊](https://aipickgold.com/card-gen/themes) · [查看定价](https://aipickgold.com/pricing) · [姐妹产品 md2wx](https://github.com/aipickgold/md2wx)

</div>

---

## ✨ 为什么选 CardMD

小红书图文贴需要把内容切成多张 3:4 卡片,手动排版要 1-2 小时。**CardMD 把这个过程压缩到 30 秒**。

- **粘贴 Markdown 自动分页** — 长文按内容量智能切卡,每页塞满不留白
- **55+ 主题 · 10 大系列** — 品牌/杂志/知识/金句/教程/封面全场景覆盖
- **Stitch 风高级工作区** — 左模板库 + 中央画布 + 右属性面板,Pro 用户精细控制水印/画布/字体/字重
- **3 个开源中文字库** — 思源宋体 / 霞鹜文楷 / 得意黑,SIL OFL 协议允许商用
- **PNG + ZIP 批量导出** — @2x 高清,可直接上传小红书图文贴
- **本地渲染 · 隐私友好** — html2canvas 在浏览器内截图,不上传任何内容

---

## 🚀 快速开始

直接浏览器使用,免注册免付费:

```
1. 打开 https://aipickgold.com/card-gen
2. 粘贴 Markdown 到左侧编辑器
3. 选主题(55+ 任选)→ 自动分页
4. 单张「导出 PNG」或批量「全部导出 ZIP」
5. 上传到小红书图文贴
```

高级模式(Pro):

```
- 顶部切换「简化 / 高级」
- 左侧按 8 大分类浏览模板(封面/资讯/金句/卡片/黑白/故事/代码)
- 中央画布:多页缩略图 + 缩放 + 全屏预览
- 右侧属性面板:水印文字+位置 / 画布 W/H / 圆角 / Padding / 字体 / 字重
```

---

## 🎨 10 大系列 · 55 主题

| 系列 | 数量 | 典型场景 |
|---|---|---|
| 🏷️ **全框品牌** | 6 | 品牌宣传、产品发布、企业报告 |
| 📰 **杂志极简** | 6 | 资讯、深度报道、热点评论 |
| 📘 **知识卡片** | 6 | 教程、考研、学习笔记 |
| 📄 **极简白底** | 6 | 长文、散文、深度观点 |
| 🎨 **莫兰迪** | 6 | 美妆、时尚、生活方式 |
| 🌙 **暗夜模式** | 6 | 科技、编程、创意设计 |
| 📡 **资讯新闻** | 5 | 财经快讯、时事评论 |
| 💬 **金句观点** | 5 | 哲思、座右铭、金句刷屏 |
| 📝 **教程步骤** | 5 | 干货指南、手把手教程 |
| 🪧 **封面首页** | 4 | 首图、开篇、标题页 |

[→ 查看全部 55 主题的完整预览](https://aipickgold.com/card-gen/themes)

---

## 📸 截图

> 截图建设中 —— 可先访问 [aipickgold.com/card-gen](https://aipickgold.com/card-gen) 看实时效果

---

## 🛠️ 技术栈

- **前端**:Next.js 16 · React 19 · TypeScript · Tailwind CSS 4
- **渲染**:自研 card-engine,1080×1440 画布,SVG 装饰层
- **导出**:html2canvas · JSZip · @2x 高清
- **字体**:jsDelivr CDN 加载 3 个 SIL OFL 字库
- **部署**:阿里云 ECS · Nginx · Next.js standalone

---

## 💎 定价

| 档位 | 价格 | 适合 |
|---|---|---|
| **免费版** | ¥0 | 个人偶尔做图 |
| **Pro 年付** | ¥79 / 年 | 活跃博主 |
| **Pro Lifetime** | ¥199 买断 | 长期小红书创作者 |
| **合并 Lifetime** | ¥299 | CardMD + [md2wx](https://github.com/aipickgold/md2wx) 两产品永久 |

Pro/Lifetime 解锁:全部 55 主题 · 移除水印 · 无限导出 · 开源字体 · 高级工作区全部控件。

[→ 完整定价方案与功能对比](https://aipickgold.com/pricing)

---

## 🗺️ 路线图

- [x] 10 大系列 55+ 主题
- [x] Stitch 风高级工作区
- [x] 3 个开源中文字库
- [x] 批量 ZIP 导出
- [ ] 自定义主题编辑器(2026 Q3)
- [ ] 移动端 Web 适配(2026 Q3)
- [ ] API 批量生成接口(2026 Q4)
- [ ] 模板市场(用户自制主题分享)

---

## ✍️ 姐妹产品

如果你也做公众号,看看我们的另一款工具:

> **[md2wx](https://github.com/aipickgold/md2wx)** — 把 Markdown 一键转微信公众号美文,40+ 主题。
>
> 两个产品共用一套账号,合并 Lifetime ¥299 一次搞定。

---

## 📜 License

MIT License · 引擎代码开源,付费主题商业授权。字体资源均为 SIL OFL 协议,允许商用嵌入。详见 [LICENSE](./LICENSE)。

---

## 👤 作者

由 **[宸的拾金笔记](https://aipickgold.com/about)** 独立开发维护。

- 🌐 **官网**:[aipickgold.com](https://aipickgold.com)
- 📢 **公众号**:宸的拾金笔记
- ✉️ **邮箱**:hello@aipickgold.com
- 💚 **微信**:待补充 (即将开放,可先邮件预约)

---

<div align="center">

**如果 CardMD 帮你做出了好看的小红书图文,请点个 ⭐ Star 支持一下!**

Made with ❤️ by [宸的拾金笔记](https://aipickgold.com) · 2026

</div>
