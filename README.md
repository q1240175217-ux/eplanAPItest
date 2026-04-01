# public-repo

这是已经整理好的公网发布目录，可直接用于 `GitHub Pages` 静态部署。

## 当前结构

```text
public-repo/
  manifest.json
  packages/
    my-plugin-1.1.1.zip
    smart-layout-1.0.0.zip
  .nojekyll
  GITHUB_PAGES.md
```

## 用途

- `manifest.json`：客户端插件中心读取的远程清单
- `packages/`：插件 ZIP 包目录
- `.nojekyll`：让 GitHub Pages 直接按静态文件方式发布
- `GITHUB_PAGES.md`：GitHub Pages 部署说明

## 用于 GitHub Pages

把 `public-repo` 里的内容放进 GitHub 仓库根目录，然后开启 `GitHub Pages` 即可。

部署完成后，你会拿到一个地址，例如：

- `https://yourname.github.io/eplan-plugin-repo/`

客户端里配置：

- `ManifestUrl = https://yourname.github.io/eplan-plugin-repo/manifest.json`

由于当前清单里的 `packageUrl` 使用的是相对路径：

- `packages/my-plugin-1.1.1.zip`
- `packages/smart-layout-1.0.0.zip`

所以部署到任何 GitHub Pages 域名下都可以直接工作，不需要再改清单里的下载地址。

## 后续发布新插件

1. 先用 `mock-repo` 的发布脚本生成 ZIP 和清单信息
2. 把新的 ZIP 复制到 `public-repo/packages/`
3. 更新 `public-repo/manifest.json`
4. 提交并推送到 GitHub
5. GitHub Pages 自动重新发布
