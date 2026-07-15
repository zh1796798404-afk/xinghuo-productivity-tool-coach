# 跨平台兼容说明

## 兼容结论

本 Skill 使用通用目录结构，Codex 和 Claude Code 可以共用核心文件：

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

## 平台差异

| 项目 | Codex | Claude Code |
| --- | --- | --- |
| 核心文件 | `SKILL.md` | `SKILL.md` |
| 参考资料 | `references/` | `references/` |
| 平台配置 | `agents/openai.yaml` | 忽略即可 |
| 用户级目录 | `~/.agents/skills/` 或 `~/.codex/skills/` | `~/.claude/skills/` |
| 显式调用 | `$productivity-tool-coach` | `/productivity-tool-coach` |
| 核心用途 | 盘问、方案、制作、验证、交付 | 盘问、方案、制作、验证、交付 |

## 当前统一流程

1. 用户先用一句话描述痛点、重复工作或想改善的结果。
2. Skill 复述理解并提出候选目标，不把工具形式直接定案。
3. 必要时要求用户上传最小脱敏样例、截图或期望结果。
4. 用户选择简易或深入盘问。
5. 每轮只问一个会影响第一版的问题。
6. 选项通常为2到3个，包含默认推荐、推荐原因和自由输入出口。
7. 用户可以回复“按推荐继续”“我不确定”“暂时跳过”或“先给我初版方案”。
8. 每3到4轮做一次小结；用户疲劳时先整理草案。
9. 需求明确后，必要时搜索 GitHub 现成工具并评估适配度、许可证、维护状态和二开难度。
10. 需求存在多个合理方向时，必要时提供2到3个视觉辅助方案。
11. 输出制作方案，等待用户明确确认。
12. 确认后制作、验证，并提供小白使用和分享说明。

## 调用策略

本 Skill 采用显式调用优先，避免普通咨询误触发长流程。Codex 的 `agents/openai.yaml` 已关闭隐式调用；Claude Code 的具体发现策略由本地版本决定，但可以通过显式命令稳定调用。

## 验证边界

已验证：

- `SKILL.md` frontmatter 和目录结构。
- 参考文件相对路径。
- 本机 Codex 安装目录与源码一致。
- Skill Creator 快速校验通过。

当前电脑没有 Claude Code CLI，因此 Claude Code 侧完成的是目录结构和文件兼容性核对，尚未完成本机运行时实测。

本仓库当前未附加开源许可证。复制、修改、再分发或商业使用前，请先确认授权范围。
