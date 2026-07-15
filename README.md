# 星火提效工具制作教练

一个帮助用户把模糊的提效想法梳理成可制作、可使用、可分享工具的 Agent Skill。

## 能做什么

- 选择深入盘问或简易盘问模式。
- 在选择盘问模式之前，先让用户描述痛点场景和想做的工具。
- 根据需要明确要求用户拖拽文件、上传截图或提供脱敏样例。
- 通过选择题、默认推荐和自由输入逐步明确需求。
- 必要时提供2到3个视觉辅助方案。
- 在从零制作之前，先搜索 GitHub 上是否有可复用的现成项目。
- 评估现成项目的适配度、维护状态、许可证和二次开发难度。
- 让用户选择直接使用、二次开发、参考借鉴或从零制作。
- 用户确认方案后，再完成工具制作、验证、使用教学和分享指导。

## 安装

### Codex

将 `productivity-tool-coach` 文件夹复制到：

```text
~/.agents/skills/productivity-tool-coach
```

或当前 Codex 环境支持的：

```text
~/.codex/skills/productivity-tool-coach
```

调用：

```text
$productivity-tool-coach
```

### Claude Code

将 `productivity-tool-coach` 文件夹复制到：

```text
~/.claude/skills/productivity-tool-coach
```

调用：

```text
/productivity-tool-coach
```

## 目录结构

```text
productivity-tool-coach/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── intake-and-attachments.md
    ├── question-framework.md
    ├── visual-companion.md
    ├── github-reuse.md
    └── delivery-template.md
```

`agents/openai.yaml` 是 Codex 的界面配置，Claude Code 可以忽略。核心行为和参考资料位于 `SKILL.md` 与 `references/` 中。

## 当前版本

v1.2.0

当前版本默认建议用户主动调用，避免普通咨询误触发多轮盘问。

## 兼容性说明

Codex 和 Claude Code 可以复用核心 `SKILL.md` 与 `references/` 目录。不同产品的 skill 安装目录和隐式调用策略可能不同，具体以本地版本为准。

本仓库当前未附加开源许可证。使用者可以按安装说明使用；如需复制、修改、再分发或用于商业项目，请先确认授权范围。
