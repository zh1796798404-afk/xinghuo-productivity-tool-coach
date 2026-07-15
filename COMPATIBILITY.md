# 跨平台兼容说明

## 兼容结论

本 skill 的核心内容采用通用的 Agent Skill 目录结构：

```text
productivity-tool-coach/
├── SKILL.md
├── references/
│   ├── question-framework.md
│   ├── intake-and-attachments.md
│   ├── visual-companion.md
│   ├── github-reuse.md
│   └── delivery-template.md
└── agents/
    └── openai.yaml
```

Codex 和 Claude Code 都可以读取 `SKILL.md` 以及其相对路径引用的参考文件，因此核心盘问流程、模式选择、视觉辅助、确认门和交付指导可以复用。

## 平台差异

| 项目 | Codex | Claude Code |
| --- | --- | --- |
| 核心入口 | `SKILL.md` | `SKILL.md` |
| 参考资料 | `references/` | `references/` |
| 平台配置 | `agents/openai.yaml` | 忽略即可 |
| 用户级目录 | `~/.agents/skills/`；当前环境兼容 `~/.codex/skills/` | `~/.claude/skills/` |
| 显式调用 | `$productivity-tool-coach` | `/productivity-tool-coach` |
| 主要用途 | 盘问、方案、制作和交付 | 盘问、方案、制作和交付 |

## 行为说明

核心流程在两个平台上保持一致：

1. 先让用户描述痛点场景和想做的工具。
2. 必要时明确要求用户拖拽文件或上传截图。
3. 确认初始目标后，再选择深入或简易盘问模式。
4. 通过一问一答明确需求。
5. 每个选择题提供默认推荐、原因和自由输入出口。
6. 必要时提供2到3个视觉辅助方向。
7. 在适合时搜索 GitHub 现成项目，评估适配度和二次开发价值。
8. 让用户决定直接使用、二次开发、参考借鉴或从零制作。
9. 输出制作方案并等待用户明确确认。
10. 确认后制作、验证、教学和提供分享方式。

平台之间可能存在 skill 自动发现和隐式调用策略差异。为了避免长流程被误触发，建议用户主动调用。

## 本次验证边界

本次已完成：

- Codex skill 目录结构校验。
- `SKILL.md` frontmatter 校验。
- 参考文件相对路径校验。
- 桌面压缩包完整性校验。

当前电脑检测到 Codex CLI，但没有检测到 Claude Code CLI，因此 Claude Code 侧完成的是文件格式和目录结构兼容性核对，尚未进行本机运行时实测。拿到安装有 Claude Code 的环境后，建议执行一次显式调用和一次完整盘问流程作为最终验收。
