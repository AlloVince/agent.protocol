# Bootstrap — Multi-repo Super

一次性为 `<system>.super` 建立或更新总上下文。仍然只使用普通 `AGENTS.md` / `README.md` / `owner/` / `docs/`。

协议仓：https://github.com/AlloVince/agent.protocol

按 `docs/spec.md` 的文档语言规则，本次生成或更新的文档标题、说明正文及输出报告默认使用简体中文；仅当前人类指令或项目明确的语言规则可覆盖。保留模板中的默认中文文档规则，交付前检查语言；代码、命令等保留原样，不批量翻译无关文档，不修改 `owner/`。

## 任务

1. 阅读：
   - `templates/AGENTS.super.md`
   - `docs/multi-repo.md`
   - `docs/spec.md`
2. 枚举已知子仓，只读取建立系统地图所需的：
   - 子仓 `AGENTS.md`
   - README / package manifests
   - 主要边界/接口/部署配置
   - 正式 CLI 与内部 package/service 声明
3. 形成系统级最小知识：
   - 每个仓的职责/不负责什么
   - 关键依赖方向和数据流
   - 已有共享基础设施与能力在哪个仓
   - 哪些规则确实跨仓反复成立
4. 生成/更新 super 根 `AGENTS.md`，保留任务到系统目标/契约、子仓入口、共享能力和正式 CLI 的真实导航；不能只把地图留在本轮报告。按 `docs/upgrade.md` 在普通注释中记录已核实的协议参考基线，未发布修改如实标注。
   按 `docs/spec.md` 的路径规则生成导航；写入后检查正文、注释、链接和命令示例，排除个人机器路径泄露。
5. 只在有 Agent 增益时写普通 `docs/`；不强制文件名与分类树。
6. 不复制子仓内部百科；super 只保留跨仓信息。
7. 检查 leadership / copilot 两种模式是否都能工作：
   - leadership 能拆任务、分配到正确仓并做整体验收
   - copilot 能从 super 定位到正确仓，并发现共享能力
8. 对共享规则给出同步建议：哪些必须进入哪些子仓 `AGENTS.md`，哪些不需要；包括长任务定期重构与中间产物规模约束。子仓入口应能定位总仓的相关规则和共享能力。
9. 不整文件覆盖子仓；在当前人类授权范围内逐仓最小更新，无同步授权时只报告差异。已有授权不重复索要确认，未处理仓和原因必须明确报告。

## 输出

- repo map
- cross-repo capability map
- shared rules
- 已发现的重复基础设施风险
- 需要同步的子仓与原因
- 尚不确定的边界
