# Vibe Coding 工作流程 Skill

一份面向 AI 编程 Agent 的中文开发流程指南。它帮助使用者从项目想法或功能需求出发，选择合适的讨论、规格、实施和验收深度，并把已确认的决策留在可追溯的工作记录中。

本仓库提供可复用的**方法与工作模板**，不是可执行应用，也不依赖某一款 Agent 产品。维护源是 `main` 分支中的 `SKILL.md` 与 `references/`；安装到本机或其他 Agent 的副本需要单独同步。

## 适用场景

- 新项目还只有初步想法，需要讨论优点、弊端、风险和遗漏的需求。
- 想审核现有项目或 idea 是否有实际价值、要求是否矛盾、关键能力是否可实现。
- 功能范围或验收方式不清楚，需要先澄清需求，再动手实现。
- 复杂功能需要以规格驱动开发（SDD）明确行为与验收条件，再逐项按测试驱动开发（TDD）实施。
- 跨会话开发需要保存规格版本、决策、进度和验证证据。
- 小改动或缺陷修复需要选择更轻量、但仍可检查结果的流程。

这份 Skill 按任务所需能力选择工具。ChatGPT、Cursor、Codex 等产品只是可选示例；实际步骤取决于当前 Agent 能访问的文件、命令、网络和界面能力。

## 快速开始

1. 先阅读 [SKILL.md](SKILL.md)，确认这套流程是否适合当前任务和 Agent 的能力。
2. 如果要在支持 `SKILL.md` 的 Agent 中启用，先准备包含 `SKILL.md` 与完整 `references/` 的待安装目录，不包含 `.git`。安装或启用前遵守目标环境的安全扫描与权限要求；本机规则要求对该目录执行 `skillspector scan <待安装目录> --no-llm`，风险评分不高于 50 才能继续。之后将已检查的目录放入该 Agent 实际使用的 Skills 路径，并保持文件相对位置。
3. 按该 Agent 的调用方式提出任务。使用 Codex 时可直接按下节的示例调用。

4. Agent 能否自动发现这份 Skill、能否编辑文件或运行测试，取决于具体应用及其权限。无法执行的环节应保留为待办，不应报告为已完成。

仅阅读方法时，无须安装。需要跨 Agent 分发时，请先阅读[单一来源与分发规则](references/distribution.md)。

### 在 Codex 中调用

在目标项目的 Codex 对话输入框中，输入 `$vibe-coding-workflow`，后面接你的具体任务。例如：

```text
$vibe-coding-workflow 我想做一个个人阅读器。请先讨论优点、问题和遗漏的场景，调研相似开源项目，再确认首版范围与验收条件；暂时不要写代码。
```

仅需审核时可以输入：

```text
$vibe-coding-workflow 请审核这个项目的目标和现有方案：找出不合理或互相矛盾的要求、项目可能缺少价值的依据和实现阻塞点；分别给出证据、影响与修改建议。先不要改代码。
```

也可以输入 `/skills`，在 Skill 列表里选择 `vibe-coding-workflow`，然后写任务。这两种显式调用方式见 [OpenAI 官方说明](https://developers.openai.com/blog/eval-skills)。明确指定 Skill 便于确认本次使用了哪套流程；未指定时，Codex 也可能根据 Skill 的名称与描述自行选用。若列表中没有这个名称，先确认 Skill 已安装并被当前 Codex 环境发现，再在新对话中重试；仅打开 GitHub 仓库并不会让 Codex 自动加载它。

## 工作流程

1. 从 [SKILL.md](SKILL.md) 开始，判断任务属于项目或想法审核、局部改动、缺陷修复、明确功能、复杂功能，还是探索性原型。
2. 新项目先用[头脑风暴指南](references/brainstorming.md)澄清目标与约束；有基本理解后调研相似开源项目，并用[合理性审查指南](references/idea-audit.md)核对价值、矛盾与可行性。用户只要求审核现有项目或 idea 时，可以直接从合理性审查开始。
3. 对需要持续实施的复杂功能，使用 [SDD + TDD 执行规则](references/sdd-tdd.md)：确认规格与验收条件，从中设计测试，逐项经历失败测试、最小实现和重构，最后对照规格验收。
4. 需要跨会话接续时，使用[工作记录模板](references/working-note.md)保存目标、决策、规格版本、进度和证据。[工具选择指南](references/tool-map.md)提供按能力选择工具的参考。

小改动可以沿用已有需求和检查方式，不要求完整规格或一套新测试。安装到不同 Agent、更新副本或发布版本时，参照[单一来源与分发规则](references/distribution.md)；编辑仓库文件不会自动更新已安装副本。

## 文件说明

| 文件 | 内容 |
| --- | --- |
| [SKILL.md](SKILL.md) | 入口与流程选择规则 |
| [references/brainstorming.md](references/brainstorming.md) | 项目初期的人机讨论 |
| [references/idea-audit.md](references/idea-audit.md) | 项目或想法的价值、矛盾与可行性审查 |
| [references/sdd-tdd.md](references/sdd-tdd.md) | 规格、测试、实施与验收 |
| [references/tool-map.md](references/tool-map.md) | 按任务和 Agent 能力选择工具 |
| [references/working-note.md](references/working-note.md) | 跨会话工作记录模板 |
| [references/distribution.md](references/distribution.md) | 单一来源、留存与分发 |

## 项目状态与反馈

当前以中文维护，尚未创建 GitHub Release、版本标签或自动化安装器。仓库中的规则提供执行方法；某个项目是否完成验收，仍要看该项目的实际运行、测试和人工检查证据。

欢迎通过 [Issues](https://github.com/xbackhome/vibe-coding-workflow-skill/issues) 提出流程缺口、错误和新场景，也欢迎 Fork 后提交 Pull Request 改进文档。提交前请阅读[贡献指南](CONTRIBUTING.md)；仓库提供 Issue 和 PR 模板，帮助说明改动理由与实际检查。项目按 [MIT 许可证](LICENSE)发布。

## 维护与发布

本仓库是维护源；本机 Agent 的安装目录是分发目标。修改 Skill 后，应先核对源文件和目标版本，再按已获授权的范围同步或发布。

对这个**已有仓库**的常规 GitHub 更新，先用 `git remote -v` 确认 `origin` 指向 `xbackhome/vibe-coding-workflow-skill`，再检查改动、提交并执行 `git push origin main`。推送后可用 Git 返回结果或 GitHub API 核对远端提交。仅在仓库创建、登录或其他操作无法通过现有命令或 API 完成时使用浏览器；不要为了重复确认已成功的推送而打开网页。

`gh` CLI 的登录状态与 Git 凭据管理器的推送凭据是两条独立路径。某一条路径失效时，先确认目标账号与当前可用权限；不要自行切换到另一个 GitHub 账号。
