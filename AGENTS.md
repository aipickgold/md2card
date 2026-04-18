# AGENTS.md

This file gives contributing AI agents (Claude, Codex, Cursor, etc.) everything they need to safely work on this repo.

## Repo Overview

- **Name**:md2card
- **Kind**:Promotional / marketing repo — README + docs + screenshots only
- **Not**:the actual application source (that lives in the private `soarsky1991/md2wx`, `/card-gen` route)
- **Brand**:宸的拾金笔记(aipickgold.com)

## Dev Workflow

1. **Before writing anything**:read `README.md` + `CLAUDE.md` in this repo
2. **Check `CHANGELOG.md`** — if your change affects what users see, add an `Unreleased` entry
3. **Stay in scope**:this is a promo repo, don't try to add app code
4. **Image assets**:go in `assets/` — prefer PNG < 1MB, WebP < 500KB
5. **Update every PR** with a `CHANGELOG.md` entry under `[Unreleased]`
6. **Never commit**:
   - secrets(`.env`, `.env.local`, API keys)
   - binaries > 1MB that aren't intentionally added assets
   - `node_modules/` or build artifacts
   - personal editor files(`.vscode/`, `.idea/`)

## Style Conventions

- **Language**:primary `README.md` is 简体中文,`README.en.md` is mirror in English
- **Punctuation**:中文标点 + 英文之间留空格,数字前后留空格
- **Emoji**:README 标题段首用,节制使用
- **Markdown**:GitHub flavored;表格用 `|---|` 分隔,代码块标记语言

## PR Checklist

Paste this in your PR description:

```
- [ ] CHANGELOG.md 已更新(Unreleased 段)
- [ ] README.md / README.en.md 已同步
- [ ] 所有链接可解析
- [ ] 无敏感文件
- [ ] 图片资源 < 1MB
```

## Communication

- Issues:https://github.com/aipickgold/md2card/issues
- Discussions:https://github.com/aipickgold/md2card/discussions
- Email:hello@aipickgold.com(紧急)
