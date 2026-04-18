# md2card Skill · 5 分钟入门教程

本教程教你如何在 Claude Code 里用 md2card Skill,让 AI 直接帮你把长文转成小红书卡片 ZIP。

## 第一步:安装 Skill

```bash
mkdir -p .claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2card/main/skills/md2card/SKILL.md \
  -o .claude/skills/md2card.md
```

## 第二步:触发 Skill

### 触发词

- 小红书 · 图文卡片 · 出图 · 做成卡片 · xiaohongshu
- 读书笔记卡片 · 干货卡 · 金句卡 · 封面图
- CardMD · md2card

### 示例对话

```
用户:把我今天写的这段读书笔记做成 5 张小红书卡片,冰蓝主题

Claude: 好的,正在处理:
  - 主题:冰蓝(know-blue,适合干货/知识)
  - 页数:5 页(用 --- 分隔或自动分页)
  - 比例:3:4(小红书标准)

  已生成下载链接:
  🔗 https://aipickgold.com/card-gen?theme=know-blue&md=IyDorrvkuabnrJTorrDmkY/niYkx...&autoexport=zip

  点击链接 → 浏览器打开 → 3 秒自动下载 cards.zip
  解压后有 5 张 1080×1440 PNG,直接传小红书。
```

## 第三步:理解 URL 参数

Skill 产出的链接长这样:

```
https://aipickgold.com/card-gen?
  theme=know-blue              ← 主题 id(55+ 任选)
  &md=BASE64_ENCODED           ← Markdown base64 URL-safe 编码
  &autoexport=zip              ← 自动导出模式(zip 批量 / png 单页)
  &ratio=3:4                   ← 比例(3:4 / 1:1 / 9:16,默认 3:4)
```

你也可以 **去掉 `autoexport`** 参数只预览,手动导出:

```
https://aipickgold.com/card-gen?theme=know-blue&md=xxx
```

## 第四步:常见场景

### 短金句单张卡

```
用户:出一张金句卡,内容"好排版是对内容的尊重"

Skill:短内容 → quote-black 主题 → 1 页
→ 下载 card_1.png
```

### 长文 10 页

```
用户:把这篇 8000 字文章切成小红书,用教程步骤风

Skill:自动按内容量分 8-10 页 → tutorial-blue 主题
→ ZIP 包含所有页
```

### 带封面

```
用户:首张做一个"AI 工具实测"封面,剩下 4 页正文用知识冰蓝

Skill:
  - 第 1 页用 cover-sunset(封面)
  - 第 2-5 页用 know-blue(内容)
  - 用 `---` 分页
```

### 带图

```
用户:这篇文章里要插入这张图(用户粘贴本地图片)

Skill:
  - 从 Claude Code 拿到 base64 data URL
  - 插入 markdown `![](data:image/...)`
  - URL 会变长(建议图片 < 500KB)
  - 或者先传图床拿到公网 URL 更快
```

## 第五步:常见陷阱

### URL 太长

- 浏览器通常支持 2MB+ 的 URL,但超长时效率降
- 长 markdown(>5000 字)建议用 `---` 分 10 页以内,或分多次调用
- base64 膨胀约 1.33 倍,10KB markdown → ~13KB URL

### 字体加载

- 页面打开后等 3 秒让开源字体加载完(Skill 已自动等)
- 如果第一次导出字体回退了,刷新页面重试

### 自动下载被拦截

- 某些浏览器(Safari 隐私模式)会拦截程序触发的下载
- 点击链接后手动按"全部导出"按钮即可

## 主题速选

| 场景 | 推荐主题 id |
|---|---|
| 干货教程 | `know-blue` / `tutorial-blue` |
| 长文散文 | `min-black` / `min-warm` |
| 情感金句 | `quote-black` / `mor-pink` |
| 品牌产品 | `brand-red` / `cover-sunset` |
| 科技深度 | `dark-purple` / `mag-gray` |

## Pro 解锁

- 55+ 主题(vs 免费 10)
- 移除水印
- 3 个开源中文字库
- 自定义画布尺寸

订阅:[aipickgold.com/pricing](https://aipickgold.com/pricing)

---

下一步:[看 10 个使用场景](./examples.md) · [理解架构](./architecture.md)
