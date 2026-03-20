# CLAUDE.md

本文件为 Claude Code 在此仓库中工作时提供指导。

## 概览

这是杜书楷的学术个人网站，通过 GitHub Pages 托管于 `shukaidu.github.io`。这是一个静态网站，无构建系统、无依赖项、无 JavaScript——仅使用纯 HTML 和 CSS。

## 文件结构

- `index.html` — 主页（个人简介、研究兴趣）
- `research.html` — 研究亮点（含图片）
- `publications.html` — 完整论文列表
- `teach.html` — 教学页面
- `contact.html` — 联系方式页面
- `style.css` — 所有页面共用的样式表
- `CV/CV.tex` — 简历源文件（编译为 `CV/CV.pdf`，从 index.html 链接）
- `*.png`, `*.jpg` — 研究图片和个人照片，直接在 HTML 中引用

所有页面共用同一导航栏（`div.topnav`）和内容容器（`div.main`）。当前页面的导航链接标有 `class="active"`。

## 部署

推送到 `master` 分支的更改会通过 GitHub Pages 自动发布。无需构建步骤——直接编辑 HTML/CSS 文件即可。

## CV 编译

CV 源文件位于 `CV/CV.tex`。编译命令：

```
cd CV && tectonic CV.tex
```

Tectonic 通过 miniconda3 安装，可自动下载缺失的 LaTeX 宏包。

## 约定

- 每个页面通过 `<link rel="stylesheet" href="style.css">` 引用样式表（相对路径）。
- 外部链接使用 `target="_blank"`。
- `publications.html` 的列表使用 `<ol reversed>`，并手动设置 `start` 属性——添加或删除条目时需同步更新 `start` 值。
- 作者姓名中的特殊字符使用 HTML 实体（例如 `&aacute;` 表示 á）。
- `research.html` 中的图片仅使用文件名引用（无子目录），文件存放于仓库根目录。
