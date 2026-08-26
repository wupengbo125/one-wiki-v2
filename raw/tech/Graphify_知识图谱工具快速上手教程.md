# Graphify 知识图谱工具快速上手教程

Graphify 是一款将项目代码、文档、PDF 及音视频等多媒体素材自动解析并构建为**本地知识图谱（Knowledge Graph）**的工具。它支持通过图查询（Query / Path / Explain）代替传统的全局搜索（Grep/Find），能够高效地帮助开发人员和 AI 助手快速理解复杂项目架构与模块依赖。

---

## 核心亮点

1. **代码零成本离线解析**：基于 Tree-Sitter AST 进行纯本地确定性解析，代码数据不离开本地，无需 LLM API 密钥。
2. **多源混合融合**：不仅支持 36+ 种编程语言的代码解析，还能对 Markdown、PDF、图片及音视频进行语义提取并融合成同一张图谱。
3. **显式与推断边区分**：所有关联边均带有标记——`EXTRACTED`（源码中显式定义/调用）或 `INFERRED`（由 Graphify 推论解析）。
4. **与 AI Coding Assistant 深度集成**：支持 Claude Code、Codex、Cursor、Gemini CLI 等 20+ 款 AI 编程工具，并支持 MCP (Model Context Protocol) 协议。

---

## 快速上手步骤

### 第一步：安装 CLI 与助手 Skill

推荐使用 `uv` 进行隔离安装：

```bash
# 1. 安装 CLI 包 (PyPI 包名为 graphifyy)
uv tool install graphifyy

# 2. 注册 Skill 到 AI 编程助手
graphify install
```

> **提示**：若使用 `pipx`，亦可运行 `pipx install graphifyy`。若提示 `command not found`，请确保 `~/.local/bin` 已加入系统环境变量中。

### 第二步：生成知识图谱 (Ingest)

在任意项目或知识库根目录下，执行建图命令：

```bash
# 对当前目录构建知识图谱
graphify .

# （可选）仅索引代码（离线模式，跳过文档和多媒体）
graphify . --code-only
```

建图完成后，会在项目根目录生成 `graphify-out/` 文件夹，包含三个核心产物：
- **`graphify-out/graph.html`**：可交互的力导向知识图谱可视化网页（用浏览器打开，支持节点点击与社区高亮）。
- **`graphify-out/GRAPH_REPORT.md`**：项目核心概念摘要、高连接度节点（God Nodes）与潜在风险关联点。
- **`graphify-out/graph.json`**：完整图谱结构数据，供终端或 AI 助手随时查询。

### 第三步：图谱查询与探索

建图后，无需逐个翻阅源码或全文 Grep，可直接通过 CLI 查询图谱：

#### 1. 语义自然语言查询 (`query`)
查找与特定问题相关的上下文与子图：
```bash
graphify query "认证模块是如何与数据库连接的？"
```

#### 2. 最短路径追踪 (`path`)
分析任意两个组件/节点之间的依赖链条：
```bash
graphify path "APIRouter" "DatabasePool"
```

#### 3. 单概念/节点详解 (`explain`)
查看某个特定节点的所有入度/出度关联及定义位置：
```bash
graphify explain "APIRouter"
```

---

## 高级配置与常用命令

- **增量更新**：源文件修改后，使用 `--update` 参数快速刷新修改节点的边：
  ```bash
  graphify . --update
  ```
- **配置忽略文件**：新建 `.graphifyignore` 语法与 `.gitignore` 一致，用于过滤无须建图的第三方依赖或生成文件。
- **开启 MCP 独立服务**：
  ```bash
  python -m graphify.serve graphify-out/graph.json
  ```

---

## 总结

Graphify 为个人知识库与大型代码库搭建了“地图”，通过直观的节点图谱与精准的子图查询，大幅降低了在海量文档和代码中定位关键逻辑的成本。
