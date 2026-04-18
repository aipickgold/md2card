# md2card Skill for Claude Code

把长文一键变成小红书 3:4 图文卡片 ZIP。在 Claude Code 对话里完成,全程不切窗口。

## 安装

### 项目级
```bash
cd 你的项目根目录
mkdir -p .claude/skills
curl -fsSL https://raw.githubusercontent.com/aipickgold/md2card/main/skills/md2card/SKILL.md \
  -o .claude/skills/md2card.md
```

### 全局级
```bash
mkdir -p ~/.claude/skills
curl -fsSL https://raw.githubusercontent.com/aipickgold/md2card/main/skills/md2card/SKILL.md \
  -o ~/.claude/skills/md2card.md
```

## 使用

在 Claude Code 对话里说:

- "帮我把这段文字做成小红书卡片,用冰蓝主题"
- "做 5 张读书笔记图文,金句风"
- "帮我写一期关于 AI 工具的小红书分享,教程风"
- "做个夕阳封面图"

Skill 会:
1. 起草(或复用你给的)Markdown
2. 推荐主题
3. 返回一个链接 → 点开后浏览器自动下载 ZIP
4. ZIP 内包含 N 张 1080×1440 PNG,直接传小红书

## 工作原理

```
Claude Code(你的电脑) 
    ↓ 起草 markdown + 选主题
    ↓ base64 编码
    ↓ 构造 URL: aipickgold.com/card-gen?theme=xxx&md=BASE64&autoexport=zip
    
你点击链接 → 浏览器打开
    ↓ 页面读取 URL 参数
    ↓ 自动加载主题 + markdown
    ↓ 等字体加载完 (3 秒)
    ↓ 自动触发 exportAllPages() - html2canvas 渲染每页 PNG
    ↓ JSZip 打包成 cards.zip
    ↓ 自动下载
```

**我们不在服务器渲染 PNG**(阿里云 ECS 894MB RAM 跑 Puppeteer 会 OOM)。所有 PNG 生成在你的浏览器完成,保证隐私 + 节省成本。

## 姐妹 Skill

- [`md2wx`](https://github.com/aipickgold/md2wx)(公众号排版 + 一键发布到草稿箱)

---

任何问题:[issue](https://github.com/aipickgold/md2card/issues) 或邮件 soarwill06@gmail.com
