# UV 高性能 Python 包管理与全局工具链实践

## 一、为什么选择 UV？
UV（Astral 出品）基于 Rust 开发，速度比传统 `pip` / `pipx` / `poetry` 快 10~100 倍，并自带 Python 版本管理与隔离环境。

## 二、核心命令与常用模式

### 1. 全局独立 CLI 工具安装 (`uv tool`)
替代臃肿的 `pipx`，自动隔离每个工具的 Python 环境：
```bash
uv tool install ruff        # 安装极速 linter
uv tool install podman-compose # 安装容器编排
uv tool list                # 查看全局已安装工具
uv tool upgrade --all       # 一键更新全部全局工具
```

### 2. 虚拟环境与依赖管理
```bash
uv venv                     # 秒级创建 .venv
source .venv/bin/activate
uv pip install -r requirements.txt
```
