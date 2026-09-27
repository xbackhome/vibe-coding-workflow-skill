# 按任务选择工具

这些是原始材料中提到的可选工具，不是必须安装的清单。先确认当前环境有哪些能力，再选择能解决当前问题的工具。软件功能会变化，做具体推荐前查看上游文档。

| 需要解决的问题 | 可选工具 | 使用方式与边界 |
| --- | --- | --- |
| 想法模糊，需要讨论目标、用户和功能边界 | ChatGPT 网页端或当前对话 | 先统一术语，再澄清主要流程、规则和验收条件；简单需求无需启用复杂流程。 |
| 需要跨多个来源做市场、用户或竞品研究 | ChatGPT Deep Research | 给出明确的研究问题和来源范围，核对报告引用，将有证据的结论与假设分开。快速问题直接搜索或对话即可。 |
| 从零做产品或作重大技术选择 | GitHub 等上游仓库；如可用，使用 project-open-source-scout | 检查功能、维护、许可证和部署约束，决定采用、改造、借鉴或自行开发。 |
| 建立可维护的项目基础 | Git、AGENTS.md、CONTEXT.md、ADR 等项目文档 | 用 Git 记录已验证的功能节点；把长期规则、术语与重要架构决策写入适合的文档，并定期清理冲突或过期内容。 |
| 界面质量或交互复杂度高 | Google Stitch；Cursor 或其他具备图像理解能力的编程 Agent | 用 Stitch 探索并确认界面，再把设计稿、设计规则和交互要求交给 Agent 实现；运行后逐屏比较和修正，不把“一比一复刻”当作自动保证。 |
| 编写代码、修改现有项目 | Codex、Claude Code、OpenCode、Pi、Cursor 中当前可用且适合仓库的一个 | 给 Agent 规格、项目规则、相关代码和验收条件；无需同时使用全部工具。 |
| 浏览器或桌面应用需要自测 | 编程 Agent 已有的浏览器／计算机控制能力；必要时才添加相应插件 | 让 Agent 操作真实流程并记录证据，再由用户判断实际体验；不能只看代码就宣称完成。 |
| 简单功能或小型修复 | 直接对话和实现；必要时使用诊断或需求澄清 Skill | 按问题复杂度使用最短路径。若安装了 Matt Skills，可按需使用 grill-me、diagnosing-bugs 或 implement。 |
| 多轮、复杂且术语容易混乱的功能 | Matt Pocock Skills 中的 grill-with-docs → to-spec → to-tickets → implement | 已安装并决定采用这条流程时，先按上游要求运行 setup-matt-pocock-skills，配置文档和任务追踪。单会话能完成的工作可跳过 to-spec 与 to-tickets；implement 的上游文档说明它会在结束前执行 code-review。 |
| 新项目希望使用成套工程流程 | Superpowers | 可作为可选流程；维护任务只选择真正需要的步骤，避免让流程成本超过改动本身。 |
| 目标过大、路线尚不清楚，或已有架构阻碍维护 | Matt Pocock Skills 中的 wayfinder、improve-codebase-architecture；术语难懂时用 wait-what | 只在出现相应问题且已具备所需项目配置时使用；不要为普通功能强制加载全套技能。 |

安装或启用外部 Skill、插件或 Agent Skill 前，先遵守当前用户与项目的安全扫描及授权规则。当前用户要求执行 `skillspector scan <目标> --no-llm`，仅在分数不高于 50 时才能继续安装；这份工具表本身不触发安装。

## 上游资料

- [ChatGPT Deep Research 帮助文档](https://help.openai.com/en/articles/10500283-deep-research-in-chatgpt)
- [Google Stitch 介绍](https://blog.google/innovation-and-ai/models-and-research/google-labs/stitch-ai-ui-design/)
- [Cursor Agent 浏览器与设计实现文档](https://cursor.com/docs/agent/tools/browser)
- [Matt Pocock Skills 仓库与工作流](https://github.com/mattpocock/skills)
- [Superpowers 仓库](https://github.com/obra/superpowers)
