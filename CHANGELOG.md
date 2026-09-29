# Changelog

## 0.3.0 — 2026-09-29

Breaking redesign.

### Removed

- `.ai/`
- `defaults/preferences.md`
- `defaults/ai-coding.md`
- session `memory.md`
- protocol-specific `workflow/`
- 强制 docs 分类树与 `docs/index.md`

### Changed

- `AGENTS.md` 成为唯一固定 Agent 入口
- `owner/` 明确为人类长期意图，Agent 默认只读
- `docs/` 改为纯 Agent 知识库，并采用“有明确 Agent 增益才写”的准入规则
- 设计文档按未来价值落入普通 `docs/` / ADR，不再依赖专用 workflow
- 引入 reuse-first：新建能力前必须先检查仓内、workspace、内部库、正式 CLI、共享服务和 `.super` 能力
- 明确 Agent 代码的人类可读性要求
- 明确人类/Agent 共用正式 CLI；常规数据/运维能力不得靠 Agent 私有脚本
- 增加长/批处理日志要求：阶段、进度/数量、失败项、最终摘要
- 增加低成本生产默认项检查，静态/文本响应压缩为显式基线之一
- 长任务改为最终成果驱动：预声明 verifier，阶段产物可复核、可继续、可重建
- 增加重复 Agent 运行的自纠偏规则：旧 plan/TODO 不是权威
- 增加 `.super` 多仓模型与 leadership / copilot 模式
- 增加共享规则从 `.super` 到子仓的语义同步策略
- 增加 protocol 升级迁移剧本，避免覆盖项目定制
