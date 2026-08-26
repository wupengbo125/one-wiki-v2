# Tailscale‑SSH 统一SSH管理教程
> 特性：不用每台机器拷贝ssh公钥，在后台ACL统一管控登录权限；认证走Tailscale账号，不需要手动密钥。

> 注意：**仅Linux支持Tailscale‑SSH；Windows/macOS只能用原生sshd走tailscale内网**。

## 1、被登录的目标机器（Linux）
开启Tailscale内置SSH服务
```bash
sudo tailscale up --ssh
# 已运行tailscale，执行下面开启ssh
sudo tailscale set --ssh=true
```
