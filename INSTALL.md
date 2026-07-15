# 星火提效工具制作教练安装说明

版本：**v1.3.0**

这是一个跨平台 Agent Skill。核心行为位于 `productivity-tool-coach/SKILL.md`，对话规则和交付模板位于 `productivity-tool-coach/references/`。

## v1.3.0 的交互变化

本版本不再要求用户在开场一次性填写痛点、工具形式、当前流程、输入和输出。用户可以先用一句话描述最麻烦的工作，之后由 Skill 复述并逐步确认。

新增或强化了：

- 首轮低负担入口。
- 工具形式后置和候选确认。
- 5到8轮优先完成的简易盘问。
- “按推荐继续”“我不确定”“暂时跳过”等回答方式。
- 每3到4轮阶段性小结。
- 用户疲劳时自动整理方案草案。
- 最小附件请求和脱敏样例协作。

## Codex 安装

将仓库内的 `productivity-tool-coach` 文件夹复制到以下任一位置：

```text
用户级安装：~/.agents/skills/productivity-tool-coach
```

当前 Codex 桌面环境也支持：

```text
~/.codex/skills/productivity-tool-coach
```

安装后重新打开 Codex 或新建任务，然后显式调用：

```text
$productivity-tool-coach
```

本 Skill 配置为显式调用优先，不会主动接管普通对话。

## Claude Code 安装

将 `productivity-tool-coach` 文件夹复制到：

```text
用户级安装：~/.claude/skills/productivity-tool-coach
项目级安装：<项目目录>/.claude/skills/productivity-tool-coach
```

在 Claude Code 中调用：

```text
/productivity-tool-coach
```

Claude Code 会读取 `SKILL.md` 和 `references/`。`agents/openai.yaml` 是 Codex 的界面配置，不影响 Claude Code 的核心行为。

## 使用前提

- Skill 本身不需要额外的 Python 或 Node.js 依赖。
- 如果后续制作的是网页、脚本或其他工具，生成的工具可能需要对应运行环境。
- 如果要创建或修改本地文件，请在目标项目目录中调用。
- 用户可随时输入“停止盘问”“直接出方案”“按目前信息继续”或“先给我初版”。

## 最小使用示例

调用后可以这样开始：

```text
我每天要搜索 Insta360 的负面消息，再整理到 CSV 表格里。
```

不需要一次补充完整流程。Skill 会先复述理解，再询问是否进入简易或深入盘问。
