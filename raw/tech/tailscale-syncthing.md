# 多机 Tailscale 局域网与 Syncthing 双向同步操作指南

## 1. 核心原理
- **Tailscale（第一步：修路）**：构建虚拟局域网，各机设置好别名后，AI **自动从 Tailscale 抓取全网所有机器的别名与 IP 写入本机的 `/etc/hosts`**，彻底打通网络层。
- **Syncthing（第二步：通车）**：基于已打通的别名路网，双向同步 `~/onespace` 目录（Send & Receive，默认 5 分钟全量扫描）。

---

## 2. 操作流程（两阶段）

### 第一阶段：修路（Tailscale 局域网）
1. 在各机对 AI 说：`执行 tools/tailscale/readme.md`
2. **人类操作**：打开终端输出的 URL 授权登录，并在 Tailscale 控制台将所有机器改名为简短别名。
3. **AI 操作**：人类改名后回复“继续”，AI **自动抓取局域网全员别名与 IP 写入本机 `/etc/hosts`**，并提交卡片。此时局域网内所有名字互相秒通！

### 第二阶段：通车（Syncthing 双向同步）
1. **全员交名片**：在各机对 AI 说 `执行 tools/syncthing/readme.md 步骤一`（自动生成同步卡片并 `git push`）。
2. **全员一键互联**：全员名片就绪后，在各机对 AI 说 `开始互联`（自动 `git pull` 并全自动双向配对）。

---

## 3. 日常命令
- **查看局域网所有节点**：`tailscale status`
- **立即触发手动同步**：`sync`
