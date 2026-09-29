# agent.protocol

Version: 0.3.0

一套尽量贴近社区习惯、尽量少造私有结构的 Agent 工程协作约定。

目标不是让仓库拥有更多 AI 文档，而是让 Agent 在长期开发中更少误判、更少重复探索、更会复用已有基础设施，并持续产出人类可理解、可验证、可维护的成果。

## v0.3 的核心变化

v0.3 是一次结构重做，不是 v0.2 的增量补丁：

- `AGENTS.md` 是唯一固定 Agent 入口；允许按社区惯例在子目录放更近的 `AGENTS.md`
- 不再使用 `.ai/`、`preferences.md`、`memory.md`、自定义 workflow 目录
- `README.md` 与 `owner/` 面向人类；`owner/` 是长期人类意图，Agent 默认只读
- `docs/` 完全服务 Agent；没有明确 Agent 增益的内容不写
- 人类和 Agent 必须共享同一套正式 CLI / package scripts
- 新能力先找已有基础设施，尤其是内部库、CLI、workspace 包、共享服务与 `.super` 中声明的跨仓能力
- Agent 生成的代码按人类长期维护标准验收，可读性优先于“聪明”和短
- 部署不得漏掉无明显代价的成熟默认项，例如静态/文本响应压缩（若未由 CDN/反代承担）
- 长任务从最终可见成果反推；阶段必须可复核、可继续、可重建，并提供验收证据
- 支持 `<system>.super` 多仓上下文，以及 leadership / copilot 两种工作方式
- protocol 升级只同步通用规则，不覆盖项目本地约束，不自动改 `owner/`

## 推荐的业务仓结构

没有强制目录树。最小形态：

```text
project/
├── AGENTS.md       # Agent 入口与项目级工程约束
├── README.md       # 给人看的项目入口
├── owner/          # 可选；人类长期意图，Agent 默认只读
├── docs/           # 可选；只放对未来 Agent 有明确收益的知识
└── ...             # 正常源码、配置、测试
```

不要为了符合协议创建空目录、空文档或文档分类树。

## 文件职责

### `AGENTS.md`

项目级 Agent 入口。放：

- 项目目标、边界与权威顺序
- 必须长期执行的工程规则
- 任务开始前应该查看哪些真实来源
- 对复用、CLI、可读性、日志、部署、长任务、验收的硬约束

不要把它写成项目百科或历史流水账。

### `README.md`

给人看的项目介绍、使用方法与入口。可以被 Agent 阅读，但不承担 Agent 私有知识库职责。

### `owner/`

人类写给项目的长期意图、产品判断、不可被实现细节稀释的原则。它是持久的人类指导，不是 Agent 的记忆区。

Agent 默认不得创建、改写、整理或“优化” `owner/`。只有当前人类明确要求修改某个 owner 文件时才可动它。

### `docs/`

只服务未来 Agent。写入前必须回答：这段信息是否能明显减少未来误判、重复研究、上下文/Token 消耗、重建成本，或保存代码/测试难以表达的边界与决策？如果不能，不写。

详见 `docs/spec.md`。

## `preferences.md` 怎么办

删除。

`preferences.md` 不是通用社区标准。v0.3 按信息性质拆回已有载体：

- 跨工具、项目级且长期有效的工程约束 → `AGENTS.md`
- Node/Python/编译器/包管理器等真实版本 → 原生配置文件与 lockfile
- formatter/linter 风格 → formatter/linter 配置
- CI/部署事实 → CI/部署配置 + 必要的 Agent docs
- 个人层面的模型/工具偏好 → Agent/IDE 的全局用户设置，不复制进每个项目

原则是：事实尽量放回事实来源，Agent 规则只保留不能由机器配置自然表达的部分。

## Bootstrap

- 普通项目：`bootstrap/project.md`
- 多仓总上下文：`bootstrap/super.md`
- 从旧版或旧 protocol 升级：`bootstrap/upgrade.md`

Bootstrap 是一次性剧本，不需要复制进业务仓。

## 模板

- `templates/AGENTS.project.md`：普通仓根 `AGENTS.md`
- `templates/AGENTS.super.md`：`<system>.super` 根 `AGENTS.md`

模板需要按真实项目删改；不要机械复制占位项和不存在的能力。

## 多仓 `.super`

`.super` 是“总上下文仓”，不是另一个私有 Agent 运行时。它仍然只使用普通的 `AGENTS.md`、`README.md`、`owner/`、`docs/`。

它负责：

- 子仓职责与边界
- 系统级架构与数据流
- 可跨仓复用的基础设施/能力地图
- 已经反复证明有价值的共享 Agent 规则
- 跨仓任务的拆分、交接和整体验收

子仓仍由自己的 `AGENTS.md` 管理。`.super` 不能绕过子仓规则。

详见 `docs/multi-repo.md`。

## 设计原则

1. **社区文件优先**：优先 `AGENTS.md`、`README.md`、`docs/`、`owner/`，不造隐藏 AI 文件系统。
2. **规则少但硬**：高频、跨任务、能显著改变 Agent 行为的才进入协议。
3. **事实回归原生载体**：能由代码、测试、schema、配置、lockfile 表达的，不再手写一份平行真相。
4. **复用优先**：写新代码之前先找已有能力；跨仓项目先查 `.super`。
5. **同一操作面**：Agent 和人类使用同一正式 CLI，不允许 Agent 私藏运维路径。
6. **可读性是接口**：代码首先是写给未来人和未来 Agent 维护的。
7. **成果驱动长任务**：研究、逆向、脚本、Phase 都只是手段；最终验收以用户可见/可用成果为准。
8. **可回溯、可重建**：关键阶段能从明确输入重建，结论有证据链。
9. **旧计划不是事实**：重复运行 Agent 时必须重新看当前代码与产物，允许推翻旧路径。
10. **缺文档比错文档安全**：没有未来 Agent 收益就不写；过期内容应删除或修正。

## 升级传播

建议流程：

```text
agent.protocol release/tag
        ↓
单仓：语义比较当前 AGENTS.md 与新模板
        ↓
.super：先更新总仓共享规则
        ↓
只把真正跨仓、仍适用的规则同步到子仓 AGENTS.md / docs
```

不做“整包覆盖”，不自动覆盖项目本地约束，也不触碰 `owner/`。
