# 3. Orca 多电脑共用同一运行时教程（无割裂会话）

stablyai/orca。源机器A跑runtime，B/C电脑仅做UI视图；worktree、终端、agent全部跑在A，不会割裂会话。

## 网络

用 Tailscale 打通 A‑B‑C。

## 源机器A（主环境）

打开 Orca

Setting → Remote Orca Servers → Start Remote Server

保留窗口打开（关闭则服务停止，二维码/配对链接失效）

## 客户端电脑B/C

打开 Orca

Setting → Remote Orca Servers → Add Server

填入主机A配对链接完成连接

## 手机客户端

打开 Orca 手机 App

扫码主机A的二维码接入

## 核心效果

所有终端、工作区、Agent运行在主机A

所有客户端共用一套环境，不会割裂会话

## 无头Linux源机器（无桌面，ip：100.102.228.46）

orca serve --pairing-address=100.102.228.46

输出配对链接，客户端同样 Add Server 粘贴链接接入
尽量用打开桌面版，用内存省时间，而且我发现用那个命令启动，干啥都卡。
## 停止

源机器A：File → Remote Orca Servers → Stop Remote Server

## 限制

- ✅ worktree、终端输出、agent进程状态全部共享在A机器
- ⚠️ 各客户端Tab视图独立（B切tab不同步到C），但进程数据全局同步
- ❗ 不要用 SSH‑Worktree，该模式每个客户端生成独立会话，会割裂

