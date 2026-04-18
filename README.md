# md2card · 小红书图文卡片生成

<div align="center">

<br/>

**AI 时代创作者的小红书卡片神器 · Skill-first**

**在 Claude Code 对话里说一句话,出图下载一气呵成**

<br/>

[English](./README.en.md) · **简体中文**

[![Website](https://img.shields.io/badge/\u5b98\u7f51-aipickgold.com%2Fcard--gen-F43F5E?style=for-the-badge&logoColor=white)](https://aipickgold.com/card-gen)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](./LICENSE)
[![Themes](https://img.shields.io/badge/Themes-55%2B-F43F5E?style=for-the-badge)](https://aipickgold.com/card-gen/themes)
[![Stars](https://img.shields.io/github/stars/aipickgold/md2card?style=for-the-badge&logo=github&color=yellow)](https://github.com/aipickgold/md2card/stargazers)
[![Release](https://img.shields.io/github/v/release/aipickgold/md2card?style=for-the-badge&color=brightgreen)](https://github.com/aipickgold/md2card/releases)
[![Last Commit](https://img.shields.io/github/last-commit/aipickgold/md2card?style=for-the-badge)](https://github.com/aipickgold/md2card/commits/main)
[![Issues](https://img.shields.io/github/issues/aipickgold/md2card?style=for-the-badge)](https://github.com/aipickgold/md2card/issues)

<br/>

[🧠 Skill 文档](./skills/md2card/README.md) · [📚 Skill 教程](./docs/skill-tutorial.md) · [🎯 使用示例](./docs/examples.md) · [📐 架构](./docs/architecture.md) · [🌐 官网](https://aipickgold.com/card-gen) · [✍️ 姐妹产品 md2wx](https://github.com/aipickgold/md2wx)

</div>

---

## 🧠 Part 1 · 推荐用法(Claude Code Skill)

**md2card 的主要使用方式不是打开网页编辑器,而是作为 Claude Code Skill 安装。**
安装一次后,在对话里让 AI 帮你"把长文做成小红书卡片",Skill 返回一个链接,点开浏览器 3 秒自动下载 cards.zip。

### 一键安装

```bash
# 项目级
mkdir -p .claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2card/main/skills/md2card/SKILL.md \
  -o .claude/skills/md2card.md

# 全局级
mkdir -p ~/.claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2card/main/skills/md2card/SKILL.md \
  -o ~/.claude/skills/md2card.md
```

### 3 个对话示范

```
👤 "帮我把昨天写的读书笔记做成 5 张小红书卡片,冰蓝主题"

🤖 已为你准备好 5 页,主题:知识·冰蓝
   🔗 点击链接,页面 3 秒后自动下载 cards.zip:
   https://aipickgold.com/card-gen?theme=know-blue&md=xxx&autoexport=zip
```

```
👤 "出一张金句卡片:好内容配不上好排版,等于 90% 努力白费"

🤖 ✓ 短内容用金句主题,推荐 quote-black
   🔗 https://aipickgold.com/card-gen?theme=quote-black&md=xxx&autoexport=zip
   只 1 页,下载 card_1.png 即可
```

```
👤 "用封面橘红主题,标题'AI 时代的创作者工具'"

🤖 ✓ 首图 cover-sunset 主题,带渐变装饰
   🔗 https://aipickgold.com/card-gen?theme=cover-sunset&md=xxx&autoexport=zip
```

### Skill 工作流

```
Claude Code 对话
    ↓ 起草 Markdown(若没有)
    ↓ 选主题(55+ 任选,或 AI 推荐)
    ↓ base64 编码 markdown 塞进 URL 参数
    ↓
你浏览器打开链接
    ↓ 页面读 URL 参数 · 载入 markdown + 主题
    ↓ 等字体加载(3 秒)
    ↓ html2canvas 渲染每页 · JSZip 打包
    ↓
cards.zip 自动下载 ✅
```

⚠️ **服务器不做 PNG 渲染**(阿里云 ECS 894MB RAM 跑 Puppeteer 会 OOM)。所有 PNG 在你的浏览器生成,保证隐私 + 节省成本。

👉 **详细教程**:[docs/skill-tutorial.md](./docs/skill-tutorial.md) · **10 个使用场景**:[docs/examples.md](./docs/examples.md)

---

## 💻 Part 2 · 替代方案(网页 Demo)

不用 Claude Code 的用户可以走网页 —— 功能一样,手工操作。

打开 [**aipickgold.com/card-gen**](https://aipickgold.com/card-gen) → 粘贴 Markdown → 选主题 → 底部「全部导出」→ cards.zip 下载。

高级模式(Pro)解锁:
- 📊 **左边模板库** · 55+ 主题按 10 分类浏览
- 🎨 **属性面板** · 水印 + 画布 W/H + 圆角 + 字体 + 字重
- 🔤 **3 个开源中文字库** · 思源宋体 / 霞鹜文楷 / 得意黑

---

## 🎨 10 大系列 · 55 主题

| 系列 | 数量 | 典型场景 |
|---|---|---|
| 🏷️ **全框品牌** | 6 | 品牌宣传、产品发布 |
| 📰 **杂志极简** | 6 | 资讯、深度报道 |
| 📘 **知识卡片** | 6 | 教程、考研、学习笔记 |
| 📄 **极简白底** | 6 | 长文、散文、观点 |
| 🎨 **莫兰迪** | 6 | 时尚、美妆、生活 |
| 🌙 **暗夜模式** | 6 | 科技、编程、创意 |
| 📡 **资讯新闻** | 5 | 财经快讯、时事 |
| 💬 **金句观点** | 5 | 哲思、座右铭 |
| 📝 **教程步骤** | 5 | 01/02 干货指南 |
| 🪧 **封面首页** | 4 | 首图、开篇 |

👉 [aipickgold.com/card-gen/themes](https://aipickgold.com/card-gen/themes) 看全部 55 主题预览 · [docs/themes.md](./docs/themes.md) 选主题指南

---

## 📐 技术架构

```
┌──────────────────────────┐
│  用户(你)                │
│  ──────────────────────  │
│  🧠 Claude Code Skill    │  ← 首推
│        ↓                 │
└────────┼─────────────────┘
         ↓ 构造 URL
         ↓ https://aipickgold.com/card-gen?md=BASE64&theme=xxx&autoexport=zip
         ↓
┌────────┴─────────────────┐
│  浏览器(你的电脑)         │  ← 所有 PNG 在这里生成
│  html2canvas + JSZip     │
│  → cards.zip 下载        │
└──────────────────────────┘

   服务器仅托管静态文件 · 零渲染负担
```

- **用户侧**:Skill 构造 URL,或手动打开网页
- **服务器侧**:只托管 HTML/CSS/JS 静态资源,无图片存储/渲染
- **浏览器侧**:React + Tailwind + html2canvas + JSZip 全客户端

👉 [docs/architecture.md](./docs/architecture.md) 完整架构说明

---

## 💎 定价

| 档位 | 价格 | 适合 |
|---|---|---|
| **免费版** | ¥0 | 10 精选主题 + 带水印 + 每日 10 次导出 |
| **Pro 月付** | ¥19/月 | 全 55 主题 · 无水印 · 无限导出 · 高级工作区 |
| **Pro 年付** | ¥99/年 | 月付 × 12 省 63% |
| **Pro Lifetime** | ¥199 买断 | 永久 + 所有后续更新 |
| **合并 Lifetime** | ¥299 | md2card + [md2wx](https://github.com/aipickgold/md2wx) 两产品永久 |

[→ 完整定价与 FAQ](https://aipickgold.com/pricing)

---

## 🗺️ Roadmap · 🕒 CHANGELOG

- [📝 v1.1.0](./CHANGELOG.md) — 2026-04 · Skill 上线 + URL 自动导出 ZIP + 本地图片上传(编辑器)
- [🗺️ 近期 / 中期 / 长期规划](./docs/roadmap.md)

---

## ✍️ 姐妹产品

> **[md2wx](https://github.com/aipickgold/md2wx)** — 把 Markdown 一键转微信公众号美文,40+ 主题,**独家支持一键发布到公众号草稿箱**。
>
> 两产品共用账号,合并 Lifetime ¥299 一次永久拥有。

---

## 📜 License · 🤝 Contributing · 🔒 Security

- **License**:MIT(引擎代码开源,Pro 主题商业授权,字体 SIL OFL)
- **贡献**:欢迎提 Issue / PR。主题设计贡献参考 [CONTRIBUTING.md](./CONTRIBUTING.md)
- **安全**:[SECURITY.md](./SECURITY.md)

---

## 👤 作者 · 💬 联系

由 **[宸的拾金笔记](https://aipickgold.com/about)** 独立开发维护。

- 🌐 **官网**:[aipickgold.com](https://aipickgold.com)
- 📢 **公众号**:宸的拾金笔记
- ✉️ **邮箱**:soarwill06@gmail.com
- 💚 **微信**:`aipickgold`(大浪淘金)

---

<div align="center">

**如果 CardMD 帮你做出了好看的小红书图文,请点个 ⭐ Star 支持一下!**

Made with ❤️ by [宸的拾金笔记](https://aipickgold.com) · 2026

💬 [Discussions](https://github.com/aipickgold/md2card/discussions) · 🐛 [Issues](https://github.com/aipickgold/md2card/issues) · 🤝 [Contributing](./CONTRIBUTING.md) · 🔒 [Security](./SECURITY.md) · 🗺️ [Roadmap](./docs/roadmap.md)

[![Star History Chart](https://api.star-history.com/svg?repos=aipickgold/md2card&type=Date)](https://star-history.com/#aipickgold/md2card&Date)

</div>
