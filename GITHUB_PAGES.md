# GitHub Pages 部署说明

当前 `public-repo` 已经整理成可直接用于 `GitHub Pages` 的静态目录。

## 推荐仓库结构

你可以新建一个 GitHub 仓库，例如：

- `eplan-plugin-repo`

然后把 `public-repo` 里的内容放到仓库根目录：

```text
manifest.json
packages/
.nojekyll
README.md
```

也可以放到 `docs/` 目录再用 GitHub Pages 发布 `docs/`，但对你现在来说，直接放根目录最简单。

## GitHub Pages 开启方式

### 方案一：直接网页上传（最省事）

1. 在 GitHub 新建一个仓库，例如：`eplan-plugin-repo`
2. 打开仓库首页，选择 `Add file` → `Upload files`
3. 把当前 `public-repo` 里的这些内容全部上传到仓库根目录：
   - `manifest.json`
   - `packages/`
   - `.nojekyll`
   - `README.md`
4. 提交后进入仓库 `Settings`
5. 打开 `Pages`
6. 在 `Build and deployment` 里选择：
   - `Source = Deploy from a branch`
   - `Branch = main`
   - `Folder = / (root)`
7. 保存

### 方案二：本地 Git 推送

如果你想直接在本地推送，可以在 `public-repo` 目录执行：

```bash
git init
git branch -M main
git add .
git commit -m "init plugin repo"
git remote add origin https://github.com/你的用户名/eplan-plugin-repo.git
git push -u origin main
```

推送完成后，同样去仓库 `Settings` → `Pages` 中开启：

- `Source = Deploy from a branch`
- `Branch = main`
- `Folder = / (root)`

等待一会后，GitHub 会给你一个公开地址，例如：


- `https://yourname.github.io/eplan-plugin-repo/`

## 客户端怎么配置

在插件中心里，把：

- `ManifestUrl`

设置成：

- `https://yourname.github.io/eplan-plugin-repo/manifest.json`

## 为什么当前目录可以直接用

当前 `manifest.json` 里的 `packageUrl` 已经使用相对路径，例如：

- `packages/my-plugin-1.1.1.zip`
- `packages/smart-layout-1.0.0.zip`

所以部署到 GitHub Pages 后会自动解析成：

- `https://yourname.github.io/eplan-plugin-repo/packages/my-plugin-1.1.1.zip`
- `https://yourname.github.io/eplan-plugin-repo/packages/smart-layout-1.0.0.zip`

不需要再手动改成绝对地址。

## 后续更新插件

1. 在本地用 `mock-repo` 发布新 ZIP
2. 把新的 ZIP 复制到 `public-repo/packages/`
3. 更新 `public-repo/manifest.json`
4. 提交并推送到 GitHub
5. GitHub Pages 自动重新发布

## 备注

如果以后你想用自定义域名，也可以在仓库根目录加 `CNAME` 文件，但当前阶段不是必须。
