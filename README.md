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
| `layouts/partials/extend_footer.html` | 时钟、访问量、打字机、进度条、灯箱、评论、播放器 |
| `layouts/partials/extend_head.html` | 默认分享图、apple-touch-icon、PWA manifest、SW 注册 |
| `layouts/partials/share_icons.html` | 微博 / QQ / 复制链接分享按钮 |
| `static/vendor/` | 自托管的前端依赖（APlayer、Fancybox） |
| `static/manifest.json`、`static/sw.js` | PWA 清单与 Service Worker |
| `content/friends.md`、`content/projects.md` | 友链页与项目页，卡片直接写在 markdown 里 |
| `.pages.yml` | Pages CMS 配置，可在浏览器/手机上写文章 |

## 评论

评论使用 **Giscus**，配置在 `hugo.toml` 的 `[params.giscus]`，仓库与分类 ID 需与 GitHub 仓库的 Discussions 设置一致。文章页会自动插入评论区，留言板使用 `#guestbook-giscus` 容器；主题会跟随站点明暗模式切换。

## 友链与项目

两个页面都是普通 markdown 加内联 HTML 卡片，新增条目直接复制文件里的卡片结构即可。友链申请入口指向留言板和邮箱，不需要额外的数据文件。

## 搜索

搜索页支持 `/` 聚焦搜索框、`Esc` 清空，快捷键脚本在 `extend_footer.html` 第 7 节。

## 背景音乐

播放器状态（曲目、进度、音量、是否在播）存在 `localStorage` 的 `my-aplayer-state` 键里。站内跳转时会尝试自动续播；浏览器拦截自动播放时，右下角会出现「▶ 继续播放」按钮。

- 属站点内跨页续播，不是全局悬浮播放：音频文件保存在 `/music/`，不经过 Service Worker 缓存。
- 曲目列表在 `extend_footer.html` 第 6 节，改歌单直接改那里的 `audio` 数组。

## PWA

`static/manifest.json` 提供安装信息，`static/sw.js` 负责离线缓存：导航请求走网络优先，静态资源走缓存优先。安装弹窗的截图是 `static/screenshot-wide.jpg`（1280×720）和 `static/screenshot-narrow.jpg`（720×1280），改版后重新截一张替换即可。

**改完静态资源后请把 `sw.js` 里的 `CACHE` 版本号加一**（如 `whymoonbrid-v2` → `whymoonbrid-v3`），否则老访客会一直拿到旧缓存。

## 资源约定

- 图片放 `static/photos/`，优先使用 WebP；页面里用绝对路径 `/photos/xxx.webp` 引用。
- 文档放 `static/docs/`，音频放 `static/music/`。
- `static/music/` 中的音频为完整曲目，请确认拥有公开托管授权。

## 部署

推送到 `main` 后，`.github/workflows/hugo.yaml` 会安装 Hugo 0.168.0、构建并发布到 Pages。构建命令：

```bash
hugo --gc --minify --baseURL "https://whymoonbrid.github.io/"
```
