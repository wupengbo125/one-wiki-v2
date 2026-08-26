# Git 独立仓库纯净脚手架与 GitHub 直连规范

## 一、核心原则：避免嵌套 Git 仓库
在父级工作区管理多个项目时，严禁产生子仓库与父仓库嵌套追踪的冲突。

## 二、标准初始化流程
```bash
# 1. 进入目标独立项目目录
cd ~/onespace/github/my-project

# 2. 初始化纯净 Git
git init
git add .
git commit -m "init: project scaffold"

# 3. 使用 GitHub CLI (gh) 自动创建远程仓库并推送
gh repo create my-project --public --source=. --push
```
* **优势**：一条命令完成本地初始化、远程 GitHub 仓库创建与首推绑定，零手动网页配置。
