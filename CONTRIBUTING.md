# Contributing to md2card

## 欢迎贡献!

感谢你对 **md2card** 感兴趣 🎉。无论是反馈一个 bug、提一个想法、改一处文档、贡献一个主题,都对我们极有帮助。

本仓库是 md2card 的 **公开推广仓库**,主要承载 README、CHANGELOG、截图与文档。应用源代码在私有仓库。尽管如此,以下方式都受欢迎:

- 在 Issue 中反馈你遇到的问题
- 在 Discussions 里提新功能点子 / 使用心得
- 改进 README 的错别字、链接、示例
- 贡献主题预览截图 / 使用案例
- 设计新的小红书卡片配色方案

---

## 🐛 反馈 Bug

在提 Issue 之前,请先:

1. 搜索 [现有 Issues](https://github.com/aipickgold/md2card/issues) 看是否已被报告
2. 在 [aipickgold.com/card-gen](https://aipickgold.com/card-gen) 复现一次,确认是产品端问题
3. 使用 `Bug Report` 模板,提供:
   - 复现步骤(1、2、3...)
   - 预期行为 vs 实际行为
   - 环境信息:浏览器、系统、主题
   - 截图或截屏(推荐)

---

## 💡 建议功能

我们非常乐意听到新点子。请使用 `Feature Request` 模板,并写清楚:

- **动机**:为什么需要这个功能?解决什么问题?
- **建议方案**:你期望的交互和体验?
- **备选方案**:是否有其他方式达成同样目的?
- **影响范围**:会影响哪些现有功能?

优先考虑的方向:主题市场、更多分类、导出格式、模板编辑器、批量 API。

---

## 📦 PR 流程

```
1. Fork 本仓库 → 创建你的分支(feat/xxx · fix/xxx · docs/xxx)
2. 提交改动(commit 格式见下)
3. 推送到你的 fork
4. 开 Pull Request 到 `main` 分支
5. 等待 review(通常 48 小时内)
6. 根据反馈 iterate,通过后合入
```

---

## ✍️ Commit 格式

遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/):

```
<type>(<scope>): <subject>
```

- **type**:`feat` · `fix` · `docs` · `chore` · `style` · `refactor` · `test`
- **scope**:可选,如 `readme`、`changelog`、`theme`
- **subject**:简短中文或英文描述,祈使句

示例:

- `docs(readme): 修正定价链接`
- `feat(theme): 新增莫兰迪秋色系列预览图`
- `fix(link): 修复姐妹仓库链接 404`

---

## 🎨 主题贡献

本仓库虽不含主题源码,但如果你设计了好看的小红书卡片主题想让我们考虑合并到官方主题库:

1. 在 `assets/themes/` 放一张 PNG 预览(1080×1440,< 1MB)
2. 用 Issue 提出「Theme Proposal」,附:
   - 主题名字(中文 + 英文)
   - 所属系列(品牌 / 杂志 / 知识 / 极简 / 莫兰迪 / 暗夜 / 资讯 / 金句 / 教程 / 封面)
   - 配色方案(hex 色值)
   - 适用场景
   - 预览图链接
3. 我们会评估、对接原作者授权后纳入正式主题库

**主题版权**:提交预览即视为授权 md2card 在推广材料中使用,最终是否纳入主题库需双方签授权。

---

## 📝 代码风格

虽然本仓库无代码,但 docs 需要遵守:

- **中文标点规范**:中文用全角,英文数字前后留半角空格
- **Markdown**:GitHub flavored,代码块标注语言
- **链接**:用相对路径引用仓库内文件,外链用完整 URL
- **图片 alt**:必写,便于屏幕阅读器
- **Emoji**:标题和 section 起首处使用,正文节制

---

## 📮 沟通

- **首选**:[Issues](https://github.com/aipickgold/md2card/issues) 和 [Discussions](https://github.com/aipickgold/md2card/discussions)
- **紧急**:soarwill06@gmail.com
- **商业合作**:同邮箱,标题注明「合作」

我们是一个小而专注的团队,大部分 Issue 会在 24-48 小时内回复。

---

## 行为准则

本项目遵循 [Contributor Covenant v2.1](https://www.contributor-covenant.org/zh-cn/version/2/1/code_of_conduct/)。简而言之:**友善、尊重、建设性**。

再次感谢你的贡献 ❤️ 。
