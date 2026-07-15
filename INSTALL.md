# 星火提效工具制作教练

版本：v1.2.0

这是一个跨平台的 Agent Skill。核心行为写在 `productivity-tool-coach/SKILL.md`，问题框架、视觉辅助方案和交付模板放在 `references/` 中。

v1.2.0 调整了首次交互顺序：用户需要先描述痛点场景和想做的工具，必要时拖拽文件或上传截图，系统确认初始目标后再选择深入或简易盘问模式。

v1.1.0 新增 GitHub 现成方案检索链路：在决定从零制作之前，可以先搜索类似开源项目，评估适配度、许可证、维护状态和二次开发成本。

## Codex 安装

将 `productivity-tool-coach` 文件夹复制到以下任一位置：

```text
用户级安装：~/.agents/skills/productivity-tool-coach
项目级安装：<项目目录>/.agents/skills/productivity-tool-coach
```

当前这套 Codex 桌面环境也支持：

```text
~/.codex/skills/productivity-tool-coach
```

安装后重新打开 Codex，或在新的任务中调用：

```text
$productivity-tool-coach
```

本 skill 当前配置为显式调用优先，不会主动接管普通对话。

## Claude Code 安装

将 `productivity-tool-coach` 文件夹复制到：

```text
用户级安装：~/.claude/skills/productivity-tool-coach
项目级安装：<项目目录>/.claude/skills/productivity-tool-coach
```

在 Claude Code 中可以使用：

```text
/productivity-tool-coach
```

Claude Code 会读取 `SKILL.md` 和 `references/`。其中 `agents/openai.yaml` 是 Codex 的界面配置，Claude Code 可以忽略，不影响核心功能。

不同工具对 skill 的自动发现和隐式调用控制可能不同。为了保持本项目的交互体验，建议用户主动调用这个 skill，再开始盘问流程。

## 使用前提

- 不需要额外的 Python 或 Node.js 依赖。
- 如果最终制作的是网页、脚本或其他工具，生成的工具本身可能需要对应运行环境。
- 如果要创建和修改本地文件，需要在目标项目目录中调用。
