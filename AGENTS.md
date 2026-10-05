# AGENTS.md

本文件为 AI 编程助手（Codex、Claude Code 等）在此仓库中工作时提供指导。`CLAUDE.md` 只含 `@AGENTS.md`，以本文件为准。

## 概览

这是杜书楷的学术个人网站，通过 GitHub Pages 托管于 `shukaidu.github.io`。这是一个静态网站，无构建系统、无依赖项——纯 HTML 和 CSS。唯一的 JavaScript 是 `others.html` 中的一段内联 `<script>`（交互式波散射演示，绘制在 canvas 上）；其余页面不含脚本。

## 文件结构

- `index.html` — 主页（个人简介、研究兴趣）
- `research.html` — 研究亮点（含图片，并用 `<video>` 嵌入 `movie/element_learning_explainer_en.mp4`）
- `publications.html` — 完整论文列表
- `teach.html` — 教学页面
- `others.html` — 其他兴趣，含交互式波散射演示（内联 JavaScript）
- `contact.html` — 联系方式页面
- `mat684/` — MAT684 课程页（`index.html`，用 `../` 相对路径引用样式表和图标）及讲义 PDF
- `movie/element_learning_explainer_en.mp4` — element learning 讲解视频，由 `research.html` 嵌入
- `style.css` — 所有页面共用的样式表
- `favicon.svg` — 网站图标，各页面通过 `<link rel="icon">` 引用
- `CV/CV.tex` — 简历源文件（编译为 `CV/CV.pdf`，从 index.html 链接）；`CV/res.cls` 为其使用的文档类
- `*.png`, `*.jpg` — 研究图片和个人照片，直接在 HTML 中引用

所有页面共用同一导航栏（`nav.topnav`）和内容容器（`div.main`）。当前页面的导航链接标有 `class="active"`。

## 部署

推送到 `master` 分支的更改会通过 GitHub Pages 自动发布。无需构建步骤——直接编辑 HTML/CSS 文件即可。

## 本地预览

```
conda activate daily
python -m http.server 8765
```

在仓库根目录运行，然后打开 http://localhost:8765/（与 `.claude/launch.json` 的端口一致）。`http.server` 是标准库，任何 Python 环境都行。

AI 助手的 shell 里 `conda` 不在 PATH 上，且 `python3` 指向 Microsoft Store 的占位程序，改用：`~/miniforge3/envs/daily/python.exe -m http.server 8765`。

## CV 编译

CV 源文件位于 `CV/CV.tex`。在 `CV/` 目录中编译：

```
conda activate talk-slides
cd CV && tectonic CV.tex
```

AI 助手的 shell 里 `conda` 不在 PATH 上，无法 activate，改用：`cd CV && ~/miniforge3/Scripts/conda.exe run -n talk-slides tectonic CV.tex`。

Tectonic 用 Miniforge 的 `talk-slides` 环境（conda-forge），不要新建环境，也不要装进 base。`CV/environment.yml` 与 `talk_slides/environment.yml` 内容一致，在新机器上用 `conda env create -f CV/environment.yml` 即可建出同一环境。Tectonic 版本已锁定（0.17），它会自动下载对应版本的 LaTeX 宏包。

## 约定

- 每个页面通过 `<link rel="stylesheet" href="style.css">` 引用样式表（相对路径）。
- 外部链接使用 `target="_blank"`。
- `publications.html` 的列表使用 `<ol reversed>`，并手动设置 `start` 属性——添加或删除条目时需同步更新 `start` 值。
- 作者姓名中的特殊字符使用 HTML 实体（例如 `&aacute;` 表示 á）。
- `research.html` 中的图片仅使用文件名引用（无子目录），文件存放于仓库根目录。
