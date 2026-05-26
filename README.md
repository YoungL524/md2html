# md2html

> 一条命令，把 Markdown 变成好看的 HTML。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 功能

将 `.md` 文件转换为**自包含、可直接打开**的 `.html` 文件，内置两套主题：

| 主题 | 效果 | 适用场景 |
|------|------|---------|
| **docs** | 技术文档风格，带侧边栏目录、阅读进度条、代码复制按钮 | 项目文档、技术方案、README 阅读版 |
| **presentation** | 16:9 幻灯片风格，自动按 `## H2` 分页，支持键盘翻页 | 技术演示、项目汇报、快速 PPT |

---

## 作为 Skill / Plugin 使用（推荐）

本项目提供 `SKILL.md`，可作为 [skills.sh](https://skills.sh) 生态的 skill 安装到 Claude Code / Cursor 等工具中。

### 安装

```bash
npx skills add YoungL524/md2html
```

### 在 Claude Code / Cursor 里怎么用

直接用自然语言描述你的目标，并指明主题即可：

- **docs（文档）**
  - 「把 `README.md` 转成 HTML，用 `docs` 主题」
- **presentation（幻灯片）**
  - 「把 `xxx.md` 做成幻灯片，用 `presentation` 主题」

主题名固定为：

- `docs`
- `presentation`

---

## 快速开始

### 1. 安装依赖

唯一的外部依赖是 [Pandoc](https://pandoc.org/installing.html)（建议 ≥ 3.0）：

本仓库**不包含** Pandoc 二进制文件，请自行安装并确保 `pandoc` 在 PATH 中可用。

```bash
# macOS
brew install pandoc

# Windows
choco install pandoc
# 或 scoop install pandoc

# Linux
apt install pandoc
```

Python ≥ 3.10，无需安装第三方 pip 包。

### 2. 使用

```bash
# 文档版（默认）
python scripts/md_to_html.py your-file.md

# 幻灯片版
python scripts/md_to_html.py your-file.md --theme presentation

# 指定输出路径
python scripts/md_to_html.py your-file.md --theme docs -o output/doc.html

# 嵌入本地图片为 base64（生成单个自包含文件）
python scripts/md_to_html.py your-file.md --inline-images
```

如果你只是想快速验证效果，可以直接把本仓库的 `README.md` 当作 demo 输入：

```bash
python scripts/md_to_html.py README.md --theme docs
python scripts/md_to_html.py README.md --theme presentation
```

生成的 `.html` 文件可直接用浏览器打开，无需任何服务器。

---

## 主题详情

### docs — 技术文档

- 左侧固定目录（自动生成，滚动高亮）
- 顶部阅读进度条
- 代码块一键复制
- 标题锚点链接
- 响应式布局（移动端自动隐藏侧边栏）
- 打印友好

### presentation — 幻灯片

- 16:9 宽屏比例，自动适配窗口
- Markdown 的 `# H1` 作为封面标题
- 每个 `## H2` 自动成为一页 slide
- 交互方式：
  - `←` / `→` 键翻页
  - `空格` 下一页
  - 底部按钮点击
- 代码块自动加语言标签 + 深色背景
- 单页内容过长时自动出现滚动条

---

## 项目结构

```
md2html/
├── scripts/
│   └── md_to_html.py       # 核心转换脚本
├── templates/
│   ├── docs/
│   │   ├── template.html5  # Pandoc HTML5 模板
│   │   └── theme.css       # 样式
│   └── presentation/
│       ├── template.html5
│       └── theme.css
├── examples/
│   └── sample.md           # 示例 Markdown
├── .gitignore
├── LICENSE
└── README.md
```

---

## 完整参数

```
usage: md_to_html.py [-h] [-o OUTPUT] [--theme {docs,presentation}]
                     [--inline-images] [--copy-images] [--toc] [--no-toc]
                     [--katex] [--highlight-style HIGHLIGHT_STYLE]
                     [--title TITLE] [--quiet]
                     input

positional arguments:
  input                 Input .md file path.

options:
  --theme               Theme to use (default: docs)
  -o, --output          Output .html path (default: <input-stem>.html)
  --inline-images       Embed local images as base64
  --copy-images         Copy local images next to output html
  --toc / --no-toc      Enable/disable table of contents
  --katex               Render math via KaTeX CDN
  --highlight-style     Pandoc syntax highlight style (default: pygments)
  --title               Override document title
  --quiet               Suppress non-error output
```

---

## 添加新主题

1. 在 `templates/` 下新建目录，如 `templates/my-theme/`
2. 创建两个文件：
   - `template.html5` — Pandoc HTML5 模板（使用 `$body$`、`$title$` 等变量）
   - `theme.css` — 样式文件
3. 在 `scripts/md_to_html.py` 的 `VALID_THEMES` 元组中加入主题名
4. 完成，用 `--theme my-theme` 即可调用

---

## 路线图

- [x] docs 主题（技术文档）
- [x] presentation 主题（幻灯片）
- [ ] 更多内置主题（mindmap、报告、阅读模式...）
- [ ] 批量转换（目录下所有 .md 一键生成）
- [ ] 自定义配色变量（通过命令行或 YAML frontmatter）

---

## License

[MIT](LICENSE)
