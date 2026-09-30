# Changelog

## Unreleased

- 修正导航生成规则：区分运行时定位与可提交路径，禁止固化个人机器路径；模板、接入和升级统一检查，保留可迁移的跨仓导航。

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

- 根 `AGENTS.md` 成为唯一固定 Agent 入口，包含真实任务导航、正式 CLI 和共享能力入口
- `owner/` 明确为人类长期意图，Agent 默认只读
- `docs/` 只保存原生载体难以表达且有明确 Agent 增益的稳定知识，长任务不例外，不保存 session 状态
- 大改动前说明问题、已有能力缺口、最简方案、影响和验收；设计文档按未来价值落入普通 `docs/` / ADR，不再依赖专用 workflow
- 引入 reuse-first：新建能力前必须先检查仓内、workspace、内部库、正式 CLI、共享服务和 `.super` 能力
- 明确 Agent 代码的人类可读性要求
- 长任务每阶段验收前定期重构，禁止累积超长函数、超大源文件、重复/废弃实现和超大单体中间产物；按规模复用分块、流式或已有存储能力
- 明确人类/Agent 共用正式 CLI；常规数据/运维能力不得靠 Agent 私有脚本
- 增加长/批处理日志要求：阶段、进度/数量、失败项、最终摘要
- 增加低成本生产默认项检查，静态/文本响应压缩为显式基线之一
- 长任务改为最终成果驱动：预声明 verifier，阶段产物可复核、可继续、可重建
- 增加重复 Agent 运行的自纠偏规则：旧 plan/TODO 不是权威
- 增加 `.super` 多仓模型与 leadership / copilot 模式
- 增加共享规则从 `.super` 到子仓的语义同步策略
- protocol 升级区分总仓/子仓，比较旧版、新版和项目定制，处理条款删除/替代，保留参考基线并报告未同步项
- 在总仓发起一次升级默认覆盖全部已声明子仓，固定同一协议来源，逐仓执行、验证并汇总；显式范围和仅 review/预览要求优先
