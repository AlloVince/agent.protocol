# Bootstrap — Upgrade

用于把现有项目升级到 agent.protocol v0.3，尤其是从 v0.2 的 `.ai/` 结构迁移。

协议仓：https://github.com/AlloVince/agent.protocol

## 先做

1. 阅读新版本：`README.md`、`templates/AGENTS.project.md`、`docs/upgrade.md`。
2. 阅读项目当前 `AGENTS.md`、`.ai/`（若存在）、README、owner（只读）、相关 docs 与原生配置。
3. 建立“旧规则 → 新落点”表，不先删除任何内容。

## 迁移

按 `docs/upgrade.md` 分类迁移：

- 通用/项目级 Agent 规则 → `AGENTS.md`
- 可由原生配置表达的事实 → 回到原生配置，不重复写
- 对未来 Agent 有明确收益的稳定知识 → 普通 `docs/`
- 人类长期意图 → 只列出给人确认，不自动写 `owner/`
- session 进度/流水账 → 删除或仅在仍需跨 session 继续时保留最小状态
- workflow → 不迁移为新 workflow；只抽出仍有效的行为约束

## 升级检查

必须确认新 `AGENTS.md` 已覆盖：

- owner 只读与权威顺序
- reuse-first / 已有基础设施检查
- 人类可读代码
- 人类与 Agent 共用正式 CLI
- 批处理/长任务日志
- 低成本生产默认项，含静态/文本压缩责任检查
- docs 只为 Agent 增益服务
- Design/ADR 准入
- 长任务最终成果、verifier、阶段可复核/可重建
- 重复运行自纠偏、旧 plan 非权威
- 若属于 `.super`，跨仓能力与共享规则

## 删除旧结构

只有确认旧 `.ai/` 中所有有价值内容都有明确去向，且人类意图没有被误删后，才删除 `.ai/`。

## 输出

最后给：

- 迁移表
- 删除项及理由
- 新 `AGENTS.md` 关键变化
- 需要人类手工处理的 owner 内容
- 仍未解决的问题

除非人类明确要求，不自动 commit/push。
