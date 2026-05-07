# claude-skill-toolkit

[Claude Code](https://claude.com/claude-code) skill — 前端项目交付工作流，覆盖六个阶段：

1. **需求理解** — PRD 拆解、新功能 vs 优化判别、改动落点定位
2. **方案设计** — 模块拆分、组件复用、状态管理、mock 策略
3. **接口联调** — OpenAPI/Apifox 解析、TS 类型、五态 mock
4. **页面实现** — 按子模块风格写代码，禁 inline style
5. **提交前 review** — 阻塞 / 建议 / 未发现三段式
6. **地图维护** — 维护项目规范知识库（PROJECT-MAP / sub-apps / review-standards）

## 安装

### Mac / Linux / WSL

```bash
mkdir -p ~/.claude/skills/toolkit && \
  curl -fsSL https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md \
  -o ~/.claude/skills/toolkit/SKILL.md
```

### Windows PowerShell

```powershell
$dir = "$env:USERPROFILE\.claude\skills\toolkit"
New-Item -ItemType Directory -Force -Path $dir | Out-Null
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/hanzhipeng0903/claude-skill-toolkit/main/SKILL.md" -OutFile "$dir\SKILL.md"
```

## 验证

安装后在 Claude Code 里输入 `/toolkit`，能看到阶段选择提示即成功。

## 使用

```
/toolkit 需求 <PRD 链接或描述>     # 阶段一
/toolkit 方案 ...                  # 阶段二
/toolkit 接口 <Apifox 链接>        # 阶段三
/toolkit 实现 ...                  # 阶段四
/toolkit review                    # 阶段五
/toolkit 维护 ...                  # 阶段六
```

直接输 `/toolkit` 不带参数，AI 会反问进入哪个阶段。

## 项目知识层

skill 本身只含通用工作流；项目特定的规范、子模块约定、评审标准放在每个项目根的 `.claude/toolkit/` 下：

```
<项目根>/.claude/toolkit/
├── PROJECT-MAP.md          # 子应用/模块概览索引
├── sub-apps/<name>.md      # 各子应用深度地图
├── review-standards.md     # 评审标准
└── examples.md             # 阶段示例
```

详见 SKILL.md。

## 更新

重新执行上面的安装命令，会覆盖旧版本。

## 反馈

issue / PR 都欢迎。
