# OpenViking (ov) 长期记忆生命周期与多设备同步机制

## 一、系统定位
OpenViking (`ov`) 是面向开发者与 AI Agent 的显式长期记忆、知识与技能资产管理工具。

## 二、记忆生命周期模型
1. **捕获 (Capture)**：在终端或交互中通过 `ov add` / `ov remember` 捕获单条上下文片段；
2. **结构化持久化 (Persist)**：自动写入本地 Git 化的存储仓库；
3. **会话结束自动提交 (Auto-Commit)**：当交互会话结束或触发指令时，自动执行 `git add . && git commit && git push`；
4. **跨设备召回 (Recall)**：通过多端同步网，在任意新设备终端一键召回历史环境参数与命令偏好。
