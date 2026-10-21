# 部署配置与 Schema

部署配置默认位于应用仓库的 `.qiniu/deploy.yaml`。字段说明和使用要求请参阅[部署配置文件](https://developer.qiniu.com/las/13569/deployment-config)。

`main` 分支维护服务介绍及部署配置的 [v1 Schema](../schemas/v1/deploy.schema.json)，供编辑器提示和配置校验使用。在 `.qiniu/deploy.yaml` 的首行添加 Schema 引用：

```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/qiniu/deployment/main/schemas/v1/deploy.schema.json
version: 1
workingDirectory: .
installCommand: npm ci
startCommand: npm run start -- --host 0.0.0.0 --port 3000
port: 3000
healthcheck:
  path: /health
  timeoutSeconds: 60
```

Schema 提供字段提示、必填项和基础约束校验。平台还会校验配置大小（64 KiB）、YAML 层数、工作目录规范化后的仓库边界及健康检查路径的 URL 编码。Schema 中的 `default` 用于编辑器提示，实际默认值由平台应用。

上述公共 Schema 地址在文件合入 `qiniu/deployment` 的 `main` 分支后生效。本地编辑时，也可以使用相对于配置文件的路径，例如 `$schema=../schemas/v1/deploy.schema.json`。
