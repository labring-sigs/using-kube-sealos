# using-kube-sealos

使用 sealos 对接仓库的示例代码，包含一个简单的 nginx 应用。

- `applaunchpad/body.json`：提交给 sealos AppLaunchpad 接口的示例请求体。
- `k8s/nginx.yaml`：同一应用的 Kubernetes Deployment 示例，可直接用 `kubectl apply`。

快速使用：

1. 直接应用到集群：`kubectl apply -f k8s/nginx.yaml`。
2. 通过 sealos：将 AppLaunchpad 的创建接口地址和 Token 替换到下面命令，再使用 `body.json` 作为请求体：

```bash
SEALOSD_API="https://<sealos-host>/<app-launchpad-create-path>"
TOKEN="<your-token>"

curl -X POST "$SEALOSD_API" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d @applaunchpad/body.json
```

根据你的 sealos 部署实际的接口路径或鉴权方式调整即可。
