# claude-skill-toolkit

[Claude Code](https://claude.com/claude-code) skill — **6 阶段一站式前端项目交付工作流**。

> 把 PRD → 方案 → 接口 → 实现 → 评审 → 知识沉淀 串成一条链路；项目特定规范沉淀在每个项目的 `.claude/toolkit/` 下，跨项目通用的工作流规则放在本 skill。

## 安装

### 推荐：`npx skills`（cross-platform 一行）

```bash
npx skills add hanzhipeng0903/claude-skill-toolkit -g -y -a claude-code
```

需要 Node ≥ 18。`-g` 装到 user-level（`~/.claude/skills/toolkit/`），`-y` 跳过确认，`-a claude-code` 指定只装到 Claude Code（如果你机器上还有 Cursor / Codex 等其他 agent，去掉这个 flag 会一起装）。

### 备用：直接下载 SKILL.md

不想装 Node 的话直接 curl：

#### Mac / Linux / WSL

```bash
mkdir -p ~/.claude/skills/toolkit && \
  curl -fsSL https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md \
  -o ~/.claude/skills/toolkit/SKILL.md
```

#### Windows PowerShell

```powershell
$dir = "$env:USERPROFILE\.claude\skills\toolkit"
New-Item -ItemType Directory -Force -Path $dir | Out-Null
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md" -OutFile "$dir\SKILL.md"
```

装完在 Claude Code 里输入 `/toolkit`，能看到阶段选择提示即成功。

## 核心理念

**让 AI 在"项目内"工作，而不是"凭空"工作。** 工作流通用，但项目特定的子模块边界、组件规范、API 范式、反模式由每个项目自己沉淀；skill 强制 AI 先读项目地图再做事，避免凭印象给方案。

## 工作流全景

```
┌───────────────────────────────────────────────────────────────┐
│                                                               │
│   /toolkit 需求 ──→ 方案 ──→ 接口 ──→ 实现 ──→ review ──→ 维护    │
│      ①         ②       ③       ④        ⑤        ⑥        │
│   理解需求    设计      联调     落码      自查     沉淀地图       │
│      │                                              ↑         │
│      └──────────── 项目知识反哺 PROJECT-MAP ─────────┘          │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

阶段一会根据需求复杂度推荐链路：

- **完整**：① → ② → ③ → ④ → ⑤（新功能 / 大重构）
- **精简**：① → ③ → ④ → ⑤（仅接口对接）
- **极简**：① → ④ → ⑤（UI 微调 / bug 修复）
- **仅 Review**：① → ⑤（只想看分析不动代码）

用户回 `继续` 即按推荐链路自动衔接，不需重复输入 `/toolkit`。

## 用户调用速查

| 命令 | 阶段 | 说明 |
|---|---|---|
| `/toolkit 需求 <PRD/链接>` | ① | 拆解需求，区分新功能 vs 优化，给落点和路径建议 |
| `/toolkit 方案 ...` | ② | 模块拆分、组件复用（带 file:line）、状态/路由/mock |
| `/toolkit 接口 <Apifox/Swagger>` | ③ | TS 类型 + 五态 mock + 请求封装 |
| `/toolkit 实现 ...` | ④ | 按子模块风格写代码，禁 inline style |
| `/toolkit review` | ⑤ | 阻塞 / 建议 / 未发现 三段式输出 |
| `/toolkit 维护 ...` | ⑥ | 走"改动提案"格式增删改项目地图 |

直接输 `/toolkit` 不带参数，AI 会反问进入哪个阶段。

## 项目知识层

skill 只含**通用**工作流；项目特定规范放在每个项目根的 `.claude/toolkit/` 下：

```
<项目根>/.claude/toolkit/
├── PROJECT-MAP.md        # 子应用/模块概览索引
├── sub-apps/<name>.md    # 子应用深度地图（架构/组件/API/反模式/速查表）
├── review-standards.md   # 评审标准
└── examples.md           # 阶段示例
```

阶段一/二/三/四进入前 AI 都会先读对应的 PROJECT-MAP 和深度地图——读完后大多数任务无需再扫源码，显著降低 token 消耗。

## 更新

```bash
npx skills update toolkit
```

或者重新跑安装命令，会覆盖旧版本。

## 反馈

issue / PR 都欢迎。

## 许可证

[MIT](./LICENSE)
