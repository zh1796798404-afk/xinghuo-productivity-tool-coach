# 星火提效工具制作教练

一个帮助用户把业务痛点逐步梳理成可制作、可使用、可验证、可分享工具的 Agent Skill。

## 核心体验

这个 Skill 不要求用户一开始写完整需求，也不要求先决定使用网页、脚本还是 Skill。用户只需要先说出一项最麻烦、最重复或最容易出错的工作，教练会用低负担的单问题对话逐步补齐信息。

当前流程是：

```text
描述痛点或想改善的结果
→ Skill复述并提出候选目标
→ 必要时上传最小脱敏样例
→ 选择简易或深入盘问
→ 每轮只处理一个关键决定
→ 阶段性小结并允许提前出方案
→ 必要时检索 GitHub 现成工具
→ 必要时提供2到3个视觉辅助方向
→ 输出制作方案并等待明确确认
→ 制作、验证、使用教学和分享指导
```

## 主要能力

- 低负担开场：首轮只要求用户描述痛点或期望结果。
- 工具形式后置：用户不知道做成什么工具时，Skill提出候选方向，但不会擅自定案。
- 简易盘问：目标5到8轮，最多15轮，适合快速形成第一版方案。
- 深入盘问：只继续解决会阻塞制作的关键问题，并允许用户随时停止。
- 动态选择题：通常提供2到3个基于当前场景生成的选项。
- 默认推荐：每道选择题提供推荐选项、推荐原因和自由输入出口。
- 低负担回答：支持“按推荐继续”“我不确定”“暂时跳过”“先给我初版方案”。
- 阶段性小结：每3到4轮总结已确认内容、默认假设和剩余关键决定。
- 疲劳收尾：用户连续表示不确定或希望加快时，自动整理方案草案，不继续堆问题。
- 附件协作：必要时明确要求用户上传CSV、Excel、截图、样例结果或现有脚本，并优先请求最小资料。
- GitHub复用评估：检索2到5个候选项目，评估适配度、维护状态、许可证和二次开发难度。
- Visual Companion：在看实际方案比读文字更容易决策时，提供2到3个视觉或流程方向，不局限于网页。
- 确认门：用户明确确认制作方案后，才创建或修改工具。
- 小白交付：完成后说明如何使用、排查和分享。

每道选择题都保留自由输入出口：

```text
如果以上选项都不符合，可以直接输入你自己的想法。
```

## 安装

### Codex

将 `productivity-tool-coach` 文件夹复制到：

```text
~/.agents/skills/productivity-tool-coach
```

或：

```text
~/.codex/skills/productivity-tool-coach
```

新建任务后显式调用：

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

### 从 GitHub 下载

下载仓库中的 `productivity-tool-coach` 文件夹，并按照上面的平台说明复制到对应目录。安装后建议重新打开客户端或新建任务，确保读取到最新文件。

## 目录结构

```text
productivity-tool-coach/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── intake-and-attachments.md
    ├── low-burden-conversation.md
    ├── question-framework.md
    ├── visual-companion.md
    ├── github-reuse.md
    └── delivery-template.md
```

`SKILL.md` 保存核心流程和工作契约。`references/` 保存附件协作、低负担对话、问题框架、视觉辅助、GitHub复用评估和交付模板。`agents/openai.yaml` 是 Codex 界面配置，Claude Code 可以忽略。

## 当前版本

**v1.3.0**

本版本重点优化用户体验：

- 首轮从“填写完整需求”改为“用一句话描述痛点”。
- 工具形式不再要求用户提前决定。
- 盘问目标从“尽量问全”改为“尽快形成可修改的第一版方案”。
- 增加默认假设、跳过、按推荐、阶段性小结和疲劳收尾机制。

## 兼容性

Codex 和 Claude Code 共用 `SKILL.md` 与 `references/`。不同客户端的安装目录和 Skill 发现策略可能不同，建议使用显式调用。

本仓库当前未附加开源许可证。复制、修改、再分发或用于商业项目之前，请先确认授权范围。
