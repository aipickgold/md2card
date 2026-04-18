# Project: md2card

**品牌**:宸的拾金笔记(aipickgold)
**官网**:https://aipickgold.com/card-gen
**产品定位**:一键把长文切成精致的 3:4 小红书图文卡片 — 55+ 主题,Stitch 风高级工作区

## 仓库性质

这是 **推广仓库**,只承载 README、LICENSE、CHANGELOG、截图、文档等用于 GitHub 展示的元数据。
**不含应用代码**。实际代码在私有仓库 `soarsky1991/md2wx`(Next.js + TypeScript,与 md2wx 同一应用的 `/card-gen` 路由)。

## 相关链接

- 产品页:https://aipickgold.com/card-gen
- 主题画廊:https://aipickgold.com/card-gen/themes
- 定价:https://aipickgold.com/pricing
- 姐妹仓库:https://github.com/aipickgold/md2wx(微信公众号排版工具)

## PR Checklist

- [ ] 更新 `CHANGELOG.md`,版本号遵循 SemVer
- [ ] 更新 `README.md` 与 `README.en.md` 若有外部信息变化(定价、主题数量、feature)
- [ ] 所有链接可解析(官网、文档、姐妹仓库)
- [ ] 图片资源放 `assets/`,不提交大于 1MB 的单文件
- [ ] 敏感信息(.env、token、API Key)绝不提交

## Commit Format

`<type>(<scope>): <subject>`

**type**:`feat` · `fix` · `docs` · `chore` · `style`

示例:
- `docs(readme): bump theme count to 60`
- `chore(meta): enrich project metadata`
- `fix(link): correct pricing URL`
