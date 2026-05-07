# 群内分享文案

## 一句话版

```
推荐个 Claude Code 前端工作流 skill：6 阶段把 PRD → 实现 → review 串起来，项目规范沉淀在 .claude/toolkit/，跨项目复用。
仓库：https://github.com/hanzhipeng0903/claude-skill-toolkit
```

## 带安装命令版（Mac / Linux / WSL，直接发可用）

```
# Claude Code 前端工作流 skill — 6 阶段交付链路（需求 / 方案 / 接口 / 实现 / review / 地图维护）
# 项目特定规范沉淀在 .claude/toolkit/，跨项目复用

mkdir -p ~/.claude/skills/toolkit && curl -fsSL https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md -o ~/.claude/skills/toolkit/SKILL.md
```

## Windows PowerShell 版

```
# 同上，Windows 用户用这个

$dir = "$env:USERPROFILE\.claude\skills\toolkit"; New-Item -ItemType Directory -Force -Path $dir | Out-Null; Invoke-WebRequest -Uri "https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md" -OutFile "$dir\SKILL.md"
```
