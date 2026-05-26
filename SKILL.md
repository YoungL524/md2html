---
name: md2html
description: 一个极简但好用的 md→html skill。把 Markdown 一键生成自包含 HTML，内置两种样式：docs（技术文档阅读版）与 presentation（16:9 幻灯片，按 H2 分页，支持键盘翻页）。触发词：md转html、markdown转html、md to html、生成html、导出html、把这篇md做成网页、做成文档页、做成演示稿、做成ppt、slide、幻灯片。
---

# md2html

> md 是源，html 是产物。

## 能力

- **能力：md → html**
  - **docs**：技术文档风格（目录/阅读进度/代码复制）
  - **presentation**：幻灯片风格（16:9、按 `##` 分页、键盘翻页）

## 使用方式（给 Agent 的指令模板）

你可以直接对 Agent 说：

- 「把 `README.md` 转成 html，用 `docs` 主题」
- 「把 `xxx.md` 做成幻灯片，用 `presentation` 主题」
- 「输出到 `dist/xxx.html`」

## 底层命令

本 skill 底层调用：

```bash
python scripts/md_to_html.py <input.md> --theme <docs|presentation> -o <output.html>
```

## 依赖

- **pandoc**（必须，用户本机安装并加入 PATH）
- Python ≥ 3.10
