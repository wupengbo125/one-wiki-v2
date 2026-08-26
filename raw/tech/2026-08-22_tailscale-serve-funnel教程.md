# 1. Tailscale Serve 多子路径教程

## 命令

```bash
# serve：只对 Tailscale 网络内可见
tailscale serve --bg --set-path /foo http://127.0.0.1:3000
tailscale serve --bg --set-path /bar http://127.0.0.1:8096

# funnel：对公网开放，公网速度很慢，哪怕你用美国的代理去访问都很慢，还是别搞这些东西
tailscale funnel --bg --set-path /foo http://127.0.0.1:3000
tailscale funnel --bg --set-path /bar http://127.0.0.1:8096

```

## 访问

```
https://主机名.ts.net/foo = http://127.0.0.1:3000/foo
https://主机名.ts.net/bar = http://127.0.0.1:8096/bar
```

## 管理

```bash
tailscale serve status          # 查看当前状态
tailscale serve reset           # 清空所有配置
tailscale serve --set-path /foo off  # 关闭某个路径
tailscale serve --https=443 off      # 关闭根路径
```

## 限制

不能直接重定向到 `http://127.0.0.1:3000` 这种没有 app name 的路径（根路径除外）。因此：

- 最常用的 1 个服务走 HTTPS 根路径
- **其他的直接用 HTTP 域名+端口 或 IP+端口，不走 HTTPS**
- 
- HTTPS 只能是 443 端口，不能再加多的端口映射
- 非要用多端口 HTTPS 可以用 Caddy，但没必要

## 单路径

只暴露一个服务时，直接用根路径，不用 `--set-path`：

**其他的直接用 HTTP 域名+端口 或 IP+端口，不走 HTTPS**

```bash
sudo tailscale serve --bg 3000
```

访问：`https://主机名.ts.net/`

## serve vs funnel

- `serve`：只对 Tailscale 网络内设备可见，外网访问不了
- `funnel`：对公网开放，任何人都能访问

## 常见问题

**Q：需要 sudo 吗？**
A：需要。443 是 1024 以下端口，要 root 权限。

**Q：证书要自己管吗？**
A：不用。自动申请、自动续期。

**Q：谁能访问？**
A：serve 模式只有同一 Tailscale 网络的设备；funnel 模式公网可达。