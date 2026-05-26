# md2html Demo

这是一份**无敏感信息**的示例文档，用来演示 `md2html` 的两套主题：

## docs 主题

适合“可阅读、可检索”的技术文档：

- 自动目录（可选）
- 阅读进度条
- 代码块一键复制

### 示例代码

```python
def hello(name: str) -> str:
    return f"hello, {name}"
```

## presentation 主题

适合“逐页讲解”的演示稿：

- 每个 `##` 会自动变成一页 slide
- 支持 `←/→` 以及 `空格` 翻页

### 命令示例

```bash
python scripts/md_to_html.py README.md --theme docs
python scripts/md_to_html.py README.md --theme presentation
```
