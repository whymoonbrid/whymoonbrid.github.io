# whymoonbrid.github.io

个人站点，基于 [Hugo](https://gohugo.io/)（extended）+ [PaperMod](https://github.com/adityatelange/hugo-PaperMod)，通过 GitHub Actions 部署到 GitHub Pages。

- 线上地址：<https://whymoonbrid.github.io/>
- 默认分支：`main`（推送到 `main` 即自动构建部署）

## 本地开发

```bash
git clone --recurse-submodules https://github.com/whymoonbrid/whymoonbrid.github.io.git
cd whymoonbrid.github.io
hugo server -D
```

> 主题以 git submodule 形式引入，克隆时务必带 `--recurse-submodules`，否则构建会失败。

## 主题版本

`themes/PaperMod` 固定在上游提交 `969bebd`（2026-10-18）。

子模块记录的是精确 commit，不会被动跟随上游更新。升级需要显式执行：

```bash
git submodule update --remote themes/PaperMod
git add themes/PaperMod && git commit -m "chore: bump PaperMod"
```

升级后请本地 `hugo server` 检查自定义样式（`assets/css/extended/custom.css`、`layouts/partials/extend_footer.html`、`layouts/partials/share_icons.html`）是否仍然生效。

## 目录速览

| 路径 | 作用 |
|------|------|
| `hugo.toml` | 站点配置：菜单、SEO、Giscus 评论 |
| `content/` | 页面与文章（`posts/` 为博客） |
| `assets/css/extended/custom.css` | 全站自定义样式 |
| `layouts/partials/extend_footer.html` | 时钟、访问量、打字机、进度条、灯箱、Giscus、播放器 |
| `layouts/partials/extend_head.html` | 默认分享图、apple-touch-icon |
| `layouts/partials/share_icons.html` | 微博 / QQ / 复制链接分享按钮 |
| `static/vendor/` | 自托管的前端依赖（APlayer、Fancybox） |
| `.pages.yml` | Pages CMS 配置，可在浏览器/手机上写文章 |

## 资源约定

- 图片放 `static/photos/`，优先使用 WebP；页面里用绝对路径 `/photos/xxx.webp` 引用。
- 文档放 `static/docs/`，音频放 `static/music/`。
- `static/music/` 中的音频为完整曲目，请确认拥有公开托管授权。

## 部署

推送到 `main` 后，`.github/workflows/hugo.yaml` 会安装 Hugo 0.168.0、构建并发布到 Pages。构建命令：

```bash
hugo --gc --minify --baseURL "https://whymoonbrid.github.io/"
```
