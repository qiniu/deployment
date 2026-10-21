# 七牛 LAS 一键部署

本仓库用于介绍七牛 LAS 一键部署服务，并维护部署配置的 Schema 文件和部署按钮。示例应用通过独立分支提供。

## 一键部署是什么

LAS 一键部署可以将公开 GitHub 仓库中的应用部署到 Sandbox，适合演示站点、文档站点、前端应用和轻量 HTTP 服务。

平台将所选分支或 Tag 固定为完整的 Commit SHA，读取该版本中的 `.qiniu/deploy.yaml`，在 Sandbox 中执行安装和启动命令，并在健康检查通过后提供公网访问地址。

使用流程：

1. 在应用仓库中准备 `.qiniu/deploy.yaml`，配置工作目录、安装命令、启动命令、服务端口和健康检查。
2. 在 LAS 控制台选择公开 GitHub 仓库、分支或 Tag，以及部署所需的区域和 Sandbox 模板。
3. 发起部署，查看部署状态和日志，健康检查通过后访问服务地址。

服务能力、当前限制和计费规则以[官方介绍](https://developer.qiniu.com/las/13567/deployment-overview)及控制台展示为准。

## 仓库结构

```text
README.md                    # 服务介绍和使用入口
schemas/
  v1/deploy.schema.json       # v1 部署配置协议
assets/
  button.svg                 # README 部署按钮
docs/
  schema.md                  # Schema 引用与配置示例
  deploy-button.md            # 部署按钮和链接用法
```

- [部署配置与 Schema](./docs/schema.md)
- [在 README 中添加部署按钮](./docs/deploy-button.md)

## 示例应用

| 分支 | 内容 | 部署 |
| --- | --- | --- |
| [`example/vite`](https://github.com/qiniu/deployment/tree/example/vite) | Vite 前端应用及部署配置 | [![Deploy on Qiniu](./assets/button.svg)](https://portal.qiniu.com/las/deployments/new?repo=qiniu%2Fdeployment&source=branch&ref=example%2Fvite) |
| [`example/go`](https://github.com/qiniu/deployment/tree/example/go) | Go HTTP 服务及部署配置 | [![Deploy on Qiniu](./assets/button.svg)](https://portal.qiniu.com/las/deployments/new?repo=qiniu%2Fdeployment&source=branch&ref=example%2Fgo) |

选择示例分支时，应用代码和 `.qiniu/deploy.yaml` 均位于该分支中；本地运行方式见各分支的 README。

```bash
git clone --branch example/vite https://github.com/qiniu/deployment.git
# 或选择 Go 示例
git clone --branch example/go https://github.com/qiniu/deployment.git
```

## 官方文档

- [一键部署介绍](https://developer.qiniu.com/las/13567/deployment-overview)
- [完成第一次部署](https://developer.qiniu.com/las/13568/deployment-quickstart)
- [部署配置文件](https://developer.qiniu.com/las/13569/deployment-config)
- [生命周期与版本管理](https://developer.qiniu.com/las/13570/deployment-lifecycle)
- [故障排查](https://developer.qiniu.com/las/13571/deployment-troubleshooting)
