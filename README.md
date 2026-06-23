# 我的 Hugo 博客

这是一个使用 [Hugo](https://gohugo.io/) 和 [Stack](https://github.com/CaiJimmy/hugo-theme-stack) 主题的博客项目，可以本地预览，也可以通过 GitHub Actions 发布到 GitHub Pages。

## 本地预览

Windows PowerShell:

```powershell
.\hugo.exe server -D --cacheDir "$PWD\.hugo_cache"
```

如果你没有使用仓库里的 `hugo.exe`，也可以安装 Hugo 后运行：

```powershell
hugo server -D --cacheDir "$PWD\.hugo_cache"
```

然后打开 `http://localhost:1313/blog/`。

## 写新文章

```powershell
.\hugo.exe new posts/my-post/index.md
```

编辑 `content/posts/my-post/index.md`，把 `draft = true` 改成 `draft = false` 后发布。需要文章封面时，把图片放进同一个文件夹，并在 Front Matter 中设置 `image = "图片文件名.png"`。

## 发布到 GitHub Pages

1. 在 GitHub 创建一个仓库，例如 `blog`。
2. 修改 `hugo.toml` 里的 `baseURL`：
   - 项目页通常是 `https://你的用户名.github.io/blog/`
   - 用户主页仓库通常是 `https://你的用户名.github.io/`
3. 初始化并推送仓库：

```powershell
git init
git add .
git commit -m "Initial Hugo blog"
git branch -M main
git remote add origin https://github.com/你的用户名/blog.git
git push -u origin main
```

4. 在 GitHub 仓库中打开 `Settings > Pages`。
5. 将 `Build and deployment` 的 `Source` 选择为 `GitHub Actions`。
6. 等待 `.github/workflows/hugo.yaml` 完成部署。

## 目录说明

- `content/posts/`：文章 Markdown 文件。
- `content/page/archives/`、`content/page/search/`：Stack 主题的归档和搜索页。
- `themes/hugo-theme-stack/`：Stack 主题源码。
- `static/img/`：头像、封面等静态图片资源。
- `.github/workflows/hugo.yaml`：GitHub Pages 自动部署工作流。

## 常用命令

```powershell
# 构建静态文件到 public/
.\hugo.exe --minify --cacheDir "$PWD\.hugo_cache"

# 本地预览草稿
.\hugo.exe server -D --cacheDir "$PWD\.hugo_cache"

# 创建文章
.\hugo.exe new posts/example.md
```
