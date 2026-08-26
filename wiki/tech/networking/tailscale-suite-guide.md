# Tailscale 局域组网与异地穿透全栈指南

## 一、核心网络能力全景
Tailscale 基于 WireGuard 构建安全的虚拟私有网络 (Mesh VPN)，为多设备提供直连加密隧道。

## 二、关键应用实战

### 1. Tailscale SSH（免密安全登录）
* **原理**：基于 Tailscale 身份验证体系替代传统 SSH 密钥对，由 ACL 统一控制权限。
* **服务端开启**：`sudo tailscale up --ssh`
* **客户端连接**：`ssh <user>@<tailscale-ip-or-magicdns>`（无需配置 `~/.ssh/id_rsa` 与公钥注入）。

### 2. Tailscale Serve 与 Funnel（内网穿透）
* **Tailscale Serve (私网暴露)**：
  将本地端口安全映射给 Tailscale 私网内其他节点访问：
  ```bash
  tailscale serve --bg 3000   # 将本机 3000 端口映射为 https://<node-name>.ts.net
  ```
* **Tailscale Funnel (公网暴露)**：
  将本地端口穿透到公网 HTTPS（需节点在 ACL 中启用 funnel 权限）：
  ```bash
  tailscale funnel --bg 3000  # 公网用户可通过公网域名访问
  ```

### 3. Tailscale + Syncthing（全自动跨设备私有同步）
* **痛点**：公共中继速度慢、数据安全性存疑。
* **架构**：Syncthing 绑定 Tailscale IP（如 `100.x.y.z:22000`），实现多设备间 P2P 点对点最高速直连同步，彻底规避公网中继。
