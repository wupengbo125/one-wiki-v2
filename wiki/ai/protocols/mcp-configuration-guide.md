# Model Context Protocol (MCP) 跨平台配置与环境隔离

## 一、MCP 核心价值
MCP（模型上下文协议）为大模型提供标准化、类型安全的外部工具与数据源调用接口，彻底解耦模型端与工具服务。

## 二、配置规范与最佳实践
* **统一配置文件路径**：通常位于 `~/.config/claude/claude_desktop_config.json` 或各 Client 统一配置项；
* **环境变量与执行路径规范**：
  * 使用绝对路径调用服务执行文件（如 `/usr/local/bin/uvx` 或 `node`）；
  * 敏感 Token 必须通过 `env: { ... }` 字段注入，严禁明文硬编码在 command 路径中；
* **权限收敛**：仅开启当前工作区真正需要的 Server，避免挂载过量 MCP Server 导致 Context 拥挤。
