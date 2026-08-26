# 本地文件夹无嵌套上传GitHub

## 一、方法说明

实现：本地文件夹内容直接上传仓库根目录到github不一样名字的仓库
案例：本地 `skills` 文件夹 → 远程 `hermes-skills` 仓库，可任意改路径和仓库地址复用。

前置：GitHub 新建空仓库（不勾选 README、协议、gitignore）

## 二、首次上传【一键全套脚本】

直接整段复制运行，兼容本地已有远程报错，无需逐条操作

```Plain Text
cd ~/.hermes/skills
git init -b main
git remote set-url origin https://github.com/wupengbo125/xxxxxxxxx.git
git add .
git commit -m "init skills"
git push -u origin main
```

## 三、日常更新【一键同步脚本】

```Plain Text
git add .
git commit -m "update skills"
git push
```

## 四、通用替换规则

换其他文件夹/仓库，只改两处：① `cd 本地文件夹路径` ② 仓库链接，逻辑完全不变

> （注：部分内容可能由 AI 生成）
