# Claude Archive

一个极简的 Hugo 静态博客，用来归档 Claude 相关的个人日记、碎片和长文。

## 目录结构

```text
.
├── archetypes/              # hugo new 生成文章时使用的模板
├── content/
│   ├── about.md             # About 页面
│   └── posts/               # 所有文章放这里
├── layouts/                 # 极简 Hugo 模板
├── static/                  # 静态资源，例如 CSS、图片、.nojekyll
├── .github/workflows/       # GitHub Pages 自动部署
├── hugo.toml                # Hugo 配置
└── README.md
```

## 新增文章

文章统一放在 `content/posts/`。

可以用 Hugo 命令创建：

```bash
hugo new content/posts/my-new-post.md
```

也可以手动新建 Markdown 文件，例如 `content/posts/my-new-post.md`：

```markdown
---
title: "文章标题"
date: 2026-06-01
draft: false
---

这里写正文。
```

如果 `draft: true`，默认发布构建不会展示这篇文章。要发布就改成 `draft: false`。

## 本地预览

先安装 Hugo，然后在仓库根目录运行：

```bash
hugo server -D
```

浏览器打开：

```text
http://localhost:1313/
```

`-D` 会把草稿文章也显示出来。如果只想看正式发布内容，可以运行：

```bash
hugo server
```

## 发布到 GitHub Pages

第一次使用时，把这个目录推到 GitHub 仓库，并确保默认分支叫 `main`：

```bash
git init
git branch -M main
git add .
git commit -m "Initial Hugo blog"
git remote add origin git@github.com:YOUR_NAME/YOUR_REPO.git
git push -u origin main
```

然后到 GitHub 仓库设置里打开 Pages：

1. 进入 `Settings`。
2. 打开 `Pages`。
3. `Build and deployment` 的 `Source` 选择 `GitHub Actions`。

之后每次 push 到 `main`，`.github/workflows/pages.yml` 都会自动构建并部署。

## 手动构建

```bash
hugo --minify
```

生成结果会放在 `public/`，这个目录已经被 `.gitignore` 忽略，不需要提交。

## 隐私提醒

这个仓库不要提交 token、密钥、隐私聊天记录、本地绝对路径或任何不想公开的内容。GitHub Pages 发布后，站点内容默认就是公开网页。
