# 在 README 中添加部署按钮

![Deploy on Qiniu](../assets/button.svg)

将下面的 Markdown 放入应用仓库的 README，用户点击按钮后进入 LAS 部署页面，确认参数并发起部署。

### 从仓库部署

先在应用仓库的目标分支中准备 `.qiniu/deploy.yaml`，再添加按钮：

```markdown
[![Deploy on Qiniu](https://raw.githubusercontent.com/qiniu/deployment/main/assets/button.svg)](https://portal.qiniu.com/las/deployments/new?repo=OWNER%2FREPOSITORY&source=branch&ref=main)
```

- 部署链接使用七牛控制台域名 `portal.qiniu.com`。
- 将 `OWNER%2FREPOSITORY` 替换为公开 GitHub 仓库，例如 `qiniu%2Fdeployment`。
- 将 `ref` 替换为需要部署的分支名。URL 参数值需要进行 URL 编码，例如 `example/vite` 写为 `example%2Fvite`。

部署链接支持以下参数：

| 参数 | 说明 | 示例 |
| --- | --- | --- |
| `repo` | GitHub 仓库，格式为 `owner/repository` | `qiniu%2Fdeployment` |
| `source` | 引用类型：`branch` 或 `tag` | `branch` |
| `ref` | 分支名或 Tag，与 `source` 对应 | `example%2Fvite` |
| `config` | 配置文件在仓库内的相对路径；省略时使用 `.qiniu/deploy.yaml` | `.qiniu%2Fdeploy.yaml` |

例如，部署本仓库的 Vite 示例时，链接路径为：

```text
/las/deployments/new?repo=qiniu%2Fdeployment&source=branch&ref=example%2Fvite
```

### 从已发布模板部署

在 Admin 中发布模板后，可以使用模板详情链接：

```markdown
[![Deploy on Qiniu](https://raw.githubusercontent.com/qiniu/deployment/main/assets/button.svg)](https://portal.qiniu.com/las/deployments/templates/TEMPLATE_ID)
```

将 `TEMPLATE_ID` 替换为已发布模板的 ID。用户进入模板详情页后选择部署参数并发起部署。

以上示例使用主仓库的公共图片地址，在 `assets/button.svg` 合入 `qiniu/deployment` 的 `main` 分支后生效。仓库内的图片预览使用相对路径，在 fork 和主仓库中均可显示。
