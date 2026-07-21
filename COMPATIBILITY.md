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
    ├── draft-plan.md
    ├── question-framework.md
    ├── visual-companion.md
    ├── github-reuse.md
    ├── delivery-template.md
    ├── platform-sync.md
    └── upload-mode.md
```

## 平台差异

| 项目 | Codex | Claude Code |
| --- | --- | --- |
| 核心文件 | `SKILL.md` | `SKILL.md` |
| 参考资料 | `references/` | `references/` |
| 平台配置 | `agents/openai.yaml` | 忽略即可 |
| 用户级目录 | `~/.agents/skills/` 或 `~/.codex/skills/` | `~/.claude/skills/` |
| 显式调用 | `$productivity-tool-coach` | `/productivity-tool-coach` |
| 防误触发 | `openai.yaml` 关闭隐式调用 | frontmatter `disable-model-invocation: true` |
| 选择题呈现 | markdown 模板 | 优先原生选项控件（AskUserQuestion），内容与模板等价 |
| 核心用途 | 梳理、草稿、制作、验收、交付 | 梳理、草稿、制作、验收、交付 |

## 当前统一流程

1. 开场先引导用户把模型与推理档位调到最高，并请用户清晰描述想做的工具（配示范级例子，只说痛点也行）。
2. 描述完整时草稿直出（草稿即复述，用户对着草稿纠错）；描述简短时复述理解，并同轮邀请讲"最近一次"的真实经过。
3. 顺着事例邀请用户上传最小脱敏样例、截图或期望结果；没有资料不阻塞。
4. 收到事例后立即生成方案草稿并落盘 `提效工具方案.md`，模糊处标 `[待确认]`。
5. 覆盖度记分板（九维，清晰/部分/缺失）驱动提问：每轮只问一个会改变第一版做法的问题，首行标注它填草稿哪一栏。
6. 选项通常为2到3个，包含默认推荐、推荐原因和自由输入出口。
7. 每收到一个回答，立即原子写回草稿，并给一行更新反馈。
8. 答满3题或覆盖度达7/9时做一次记分板小结；问题数量动态、硬上限5问（深挖10问）；用户疲劳时先定稿草案。
9. 需求明确后，必要时搜索 GitHub 现成工具并评估适配度、许可证、维护状态和二开难度；必要时提供2到3个视觉辅助方案。结论写回草稿。
10. 草稿定稿，只展示关键决定摘要、变化和假设清单，等待用户明确确认。
11. 确认后制作；按"当…时，工具应…"的验收标准逐条核对并给出证据。
12. 工具形式简单高效优先（图形界面优先、零依赖优先）；交付手册用"第一步/第二步"分步格式、零术语。
13. 交付后进入试用与微调闭环：手动/自动测试可选（自动不替代上手），反馈微调直到用户明确满意；再次调用时走迭代短流程。
14. 平台协同（本地配置存在时启用）：制作过程元数据静默同步星火平台制作记录；用户满意后可选择把工具打包上传回平台并登记工具表。
15. 上传模式：首条消息为上传意图或拖入完整工具目录时，只读解析生成上架字段 → 一屏确认 → 上传登记（来源渠道=存量工具插件上传，不创建制作记录）。

## 调用策略

本 Skill 采用显式调用优先，避免普通咨询误触发长流程。Codex 的 `agents/openai.yaml` 已关闭隐式调用；Claude Code 的 `SKILL.md` frontmatter 已设置 `disable-model-invocation: true`，仅响应 `/productivity-tool-coach` 显式调用。

## 验证边界

已验证：

- `SKILL.md` frontmatter 为合法 YAML，字段包含 `name`、`description`、`disable-model-invocation`。
- 目录结构与全部参考文件相对路径有效。
- 本机 Codex 安装目录、Claude Code 安装目录与源码逐文件一致。
- 旧版概念（模式选择、轮数上限口径、重复开场白拷贝）无残留。

完整对话流程的运行时实测（真实用户场景走查）建议在两类典型任务上进行：CSV 批处理工具、网页小工具。

本仓库当前未附加开源许可证。复制、修改、再分发或商业使用前，请先确认授权范围。
