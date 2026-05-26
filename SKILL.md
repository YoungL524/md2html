---
name: md2html
description: 一个极简的 md → html 转换 skill。基于 Pandoc + 两套主题（docs/presentation），把 Markdown 一键加工成可发布的 HTML：文档版（带目录、复制代码、阅读进度）或幻灯片版（16:9，按 H2 自动分页，键盘翻页）。触发词：md转html、markdown转html、生成html、做成网页、做成文档页面、做成ppt、幻灯片、slide。
---

# md2html

> md 是源文件，html 是产物。

## 能力

- **能力**：把 `.md` 转为 `.html`
- **主题**：
  - `docs`：技术文档阅读版（可选 TOC）
  - `presentation`：16:9 幻灯片（按 `##` 分页）

## 使用方式（底层命令）

```bash
python scripts/md_to_html.py input.md --theme docs -o output.html
python scripts/md_to_html.py input.md --theme presentation -o output.html
```

## 依赖

- 需要本机安装 `pandoc` 并在 PATH 中可用
- 需要 Python ≥ 3.10
