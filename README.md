# 个人空间

一个 Hugo 静态网站，布局参考早期个人空间的横幅、资料栏和日志区。文章保存在 `content/`，外观保存在 `layouts/` 与 `assets/`，不依赖第三方主题或在线编辑器。

## 本地运行

安装 Hugo 0.168.0 后，在项目目录运行：

```bash
hugo server -D
```

然后打开 `http://localhost:1313/`。构建正式站点运行 `hugo --minify`，结果在 `public/`。

## 发文章（当前版本）

当前没有网站内的“发帖”按钮：GitHub Pages 只能展示静态页面，不会在网页里保存新文章。文章源文件是 `content/posts/` 下的 Markdown。

**在 GitHub 网页发布**：进入仓库的 `content/posts/` 目录，点 **Add file → Create new file**，文件名填 `文章名.md`；正文开头按以下格式填写，设置 `draft = false`，提交到 `main` 后自动构建：

```markdown
+++
title = '文章标题'
date = 2026-10-22T09:00:00+08:00
draft = false
+++

这里写正文，支持 Markdown。
```

**在本地发布**：在项目目录运行 `hugo new content posts/文章名.md`，编辑文件并将 `draft = false`，然后运行 `git add content/posts && git commit -m "post: 新文章" && git push`。日期由 Hugo 自动填写。本地预览用 `hugo server -D`（可预览草稿）。后续若需要更自由的排版和浏览器编辑体验，可另接入编辑器，但仍以 Markdown 文件为文章原件。

## 改自己的内容

- 站名、昵称和空间心情：`hugo.toml`（当前“小梨”等名称仅为待替换的示例）
- 首页介绍：`content/_index.md`
- 关于我：`content/about.md`
- 日志：`content/posts/`，可修改或删除 `first-post.md` 示例
- 相册介绍：`content/albums/_index.md`
- 横幅、导航、侧栏：`layouts/_partials/`
- 配色和版式：`assets/css/space.css`

日志和相册目前只包含静态内容，不提供登录、留言或上传服务。不要提交个人隐私、口令或密钥到公开仓库。

## 发布

`.github/workflows/pages.yml` 会在推送 `main` 时用 Hugo 构建并部署。首次使用，在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。网站地址为 `https://quqxiaoli.github.io/`。
