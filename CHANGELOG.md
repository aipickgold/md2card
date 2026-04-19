# Changelog

All notable changes to **md2card** are documented here. This project follows [Semantic Versioning](https://semver.org/) and the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

## [v1.2.0] · 2026-04-19

### Added
- 🔑 **Pro API Key 鉴权系统上线** · 购买后通过微信客服 `aipickgold` 接收 `CMWX-XXXX-XXXX-XXXX` 格式的 API Key
- 🧠 Skill URL 模板新增 `&key=<LICENSE>` 参数,Claude 从 `MD2CARD_LICENSE_KEY` 环境变量读取
- 🌐 Web 编辑器右侧新增**圆形 Pro 按钮**(免费状态会 pulsing 提示,点击弹出激活框)
- 🔒 免费版导出自动带 "宸的拾金笔记 · aipickgold.com" 水印;Pro 无水印
- 🛡️ `?key=` URL 参数在进入页面 50ms 内被 `history.replaceState` 剥离,避免进浏览器历史 / Referer / 分享截图
- 🛡️ Nginx access log 脱敏:不再记录 query string(防 key 意外入日志)

### Changed
- SKILL.md URL 模板默认包含 `&key=$MD2CARD_LICENSE_KEY`,无 key 时落到带水印免费版
- 激活状态在同设备 localStorage 缓存 7 天,过期自动后台 re-verify

### Notes
- bundle-lifetime(合并 Lifetime ¥299)的 key 同时解锁 md2wx + md2card
- 产品独立 key 按产品作用域校验,跨产品使用会返回 `wrong_product`
- 数据隐私:License 数据只保存在作者的阿里云 ECS,不使用第三方数据库

## [v1.1.0] · 2026-04-18

### Added
- 🧠 **Claude Code Skill 官方上线**(`skills/md2card/SKILL.md`)· 对话式让 AI 做小红书卡片
- 🔗 `/card-gen` 页面支持 **URL 参数自动载入 + 自动导出 ZIP**(`?md=base64&theme=xxx&autoexport=zip`)
- 📷 编辑器**本地图片上传**(base64 inline,不上传服务器)
- 📚 `docs/skill-tutorial.md` · `docs/examples.md`(10 场景)· `docs/architecture.md`
- 默认示例改为 5 页内容,展示封面/列表/表格/金句/CTA 各种能力
- README 全面改版为 Skill-first 结构

### Architecture
- 明确 Skill → 浏览器(html2canvas)的渲染路径
- 服务器不跑 headless Chrome,保持 894MB RAM 实例稳定

### Notes
- 订阅价格不变
- 主题和引擎 schema 向后兼容

## [Unreleased]

### Planned
- 自定义主题编辑器(2026 Q3)
- 移动端 Web 适配(2026 Q3)
- API 批量生成接口(2026 Q4)
- 模板市场(用户自制主题分享)

---

## [v0.4.0] - 2026-04

封面系列重设计 + 三个开源中文字库 + 独立子站。

### Added
- 封面首页系列重设计,4 款新主题聚焦「首图 / 开篇 / 标题页」场景
- 3 个开源中文字库(SIL OFL 协议,允许商用嵌入):
  - 思源宋体 Source Han Serif
  - 霞鹜文楷 LXGW WenKai
  - 得意黑 Smiley Sans
- 独立子站 `aipickgold.com/card-gen`,与 md2wx 共用账号体系

### Changed
- 字体从 jsDelivr CDN 加载,首屏优化
- 水印/画布/字体/字重等高级控件重新归类到属性面板

---

## [v0.3.0] - 2026-03

Stitch 风高级工作区上线,主题扩展到 55 款。

### Added
- Stitch 风工作区:左模板库 + 中央画布 + 右属性面板
- 55 主题 × 10 大系列:全框品牌 / 杂志极简 / 知识卡片 / 极简白底 / 莫兰迪 / 暗夜模式 / 资讯新闻 / 金句观点 / 教程步骤 / 封面首页
- Pro 用户精细控制:水印文字与位置、画布 W/H、圆角、Padding、字体、字重
- 多页缩略图 + 缩放 + 全屏预览

### Changed
- 简化模式与高级模式可顶部切换
- 左侧按 8 大分类浏览模板

---

## [v0.2.0] - 2026-02

18 主题,自动分页,批量导出。

### Added
- 18 款主题
- 智能分页算法:长文按内容量自动切成多张 3:4 卡片
- 单张 PNG 导出(@2x 高清)
- 批量 ZIP 导出
- html2canvas 本地截图,不上传内容

### Fixed
- 修复长标题换行导致的溢出
- 修复 Safari 下字体加载闪烁

---

## [v0.1.0] - 2026-01

MVP 首发。

### Added
- Markdown 粘贴 → 生成 3:4 小红书图文卡片
- 基础 5 款主题
- 1080 × 1440 画布,SVG 装饰层
- 实时预览 + 单张导出

[Unreleased]: https://github.com/aipickgold/md2card/compare/v0.4.0...HEAD
[v0.4.0]: https://github.com/aipickgold/md2card/releases/tag/v0.4.0
[v0.3.0]: https://github.com/aipickgold/md2card/releases/tag/v0.3.0
[v0.2.0]: https://github.com/aipickgold/md2card/releases/tag/v0.2.0
[v0.1.0]: https://github.com/aipickgold/md2card/releases/tag/v0.1.0
