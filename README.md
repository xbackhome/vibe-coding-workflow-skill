# Vibe Coding 工作流程 Skill

一份面向 AI 编程 Agent 的中文开发流程指南。它帮助使用者从项目想法或功能需求出发，选择合适的讨论、规格、实施和验收深度，并把已确认的决策留在可追溯的工作记录中。

## 适用场景

- 新项目还只有初步想法，需要讨论优点、弊端、风险和遗漏的需求。
- 功能范围或验收方式不清楚，需要先澄清需求，再动手实现。
- 复杂功能需要以规格驱动开发（SDD）明确行为与验收条件，再逐项按测试驱动开发（TDD）实施。
- 跨会话开发需要保存规格版本、决策、进度和验证证据。
- 小改动或缺陷修复需要选择更轻量、但仍可检查结果的流程。

这份 Skill 按任务所需能力选择工具。ChatGPT、Cursor、Codex 等产品只是可选示例；实际步骤取决于当前 Agent 能访问的文件、命令、网络和界面能力。

## 如何使用

1. 从 [SKILL.md](SKILL.md) 开始，判断任务属于局部改动、缺陷修复、明确功能、复杂功能，还是探索性原型。
2. 新项目或重大技术选择先调研相似开源项目；想法尚不明确时，使用[头脑风暴指南](references/brainstorming.md)讨论价值、问题和遗漏的场景。
3. 对需要持续实施的复杂功能，使用 [SDD + TDD 执行规则](references/sdd-tdd.md)：确认规格与验收条件，从中设计测试，逐项经历失败测试、最小实现和重构，最后对照规格验收。
4. 需要跨会话接续时，使用[工作记录模板](references/working-note.md)保存目标、决策、规格版本、进度和证据。[工具选择指南](references/tool-map.md)提供按能力选择工具的参考。

小改动可以沿用已有需求和检查方式，不要求完整规格或一套新测试。安装到不同 Agent、更新副本或发布版本时，参照[单一来源与分发规则](references/distribution.md)；编辑仓库文件不会自动更新已安装副本。

## 文件说明

| 文件 | 内容 |
| --- | --- |
| [SKILL.md](SKILL.md) | 入口与流程选择规则 |
| [references/brainstorming.md](references/brainstorming.md) | 项目初期的人机讨论 |
| [references/sdd-tdd.md](references/sdd-tdd.md) | 规格、测试、实施与验收 |
| [references/tool-map.md](references/tool-map.md) | 按任务和 Agent 能力选择工具 |
| [references/working-note.md](references/working-note.md) | 跨会话工作记录模板 |
| [references/distribution.md](references/distribution.md) | 单一来源、留存与分发 |

## 维护与发布

本仓库是维护源；本机 Agent 的安装目录是分发目标。修改 Skill 后，应先核对源文件和目标版本，再按已获授权的范围同步或发布。安装或启用新的 Skill 前，遵守目标环境的安全扫描要求。

对这个**已有仓库**的常规 GitHub 更新，先用 `git remote -v` 确认 `origin` 指向 `xbackhome/vibe-coding-workflow-skill`，再检查改动、提交并执行 `git push origin main`。推送后可用 Git 返回结果或 GitHub API 核对远端提交。仅在仓库创建、登录或其他操作无法通过现有命令或 API 完成时使用浏览器；不要为了重复确认已成功的推送而打开网页。

本机 `gh` CLI 的登录状态与 Git 凭据管理器的推送凭据是两条独立路径。某一条路径失效时，先确认目标账号与当前可用权限；不要自行切换到另一个 GitHub 账号。
