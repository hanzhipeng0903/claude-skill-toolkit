# CLAUDE.md

本仓库是 Claude Code skill 单文件分发，唯一对外产物是 `SKILL.md`。用户安装后该文件落到 `~/.claude/skills/toolkit/SKILL.md`，CC 启动时全文加载进 prompt。

## 改动 SKILL.md 时

- 保持中文为主、英文术语（PRD / mock / review 等）原样，不要翻译已确立的中文章节标题
- 改"阶段路由表"前先 grep 全文确认所有交叉引用同步
- 不要给 SKILL.md 加 frontmatter 之外的元信息（如 `version`、`lastUpdated`）——加载时会吃 token
- 修改后用 `wc -l SKILL.md` 确认行数；目标控制在 500 行以内

## 不要做

- 不要把 README 内容塞进 SKILL.md（README 给人看，SKILL.md 给 AI 读）
- 不要在 SKILL.md 里加装饰性 emoji；现有的 ⚠️ 是约束信号，不算装饰
- 不要新增"必须使用某个 MCP"的硬绑定——保持工具中立，让用户环境里有什么就用什么
- 不要把项目特定规范（焦点科技、aise 等）写进 SKILL.md；这些只属于各项目自己的 `.claude/toolkit/`

## 验证

改完后建议在另一个真实前端项目里跑一次 `/toolkit 需求 <任意 PRD>`，确认阶段路由还正常工作再 push。
