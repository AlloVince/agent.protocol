# Bootstrap · Standard

一次性接入。完成后靠 AGENTS + docs + workflow 自持，不再依赖本文件。
协议：https://github.com/AlloVince/agent.protocol
角色：建工程知识体系，不是写业务代码。中文、紧凑、不编造。

## 目标
新 session 只读 AGENTS 即可按需加载，达到接近熟练工程师的规范与项目地图（深度取决于首扫质量）。

## 1. 模式
**A 新项目** | **B 已有项目**。不假设；不清则问。

## 2. 拉取协议
获取协议仓，读结构、templates、defaults、workflow、memory.template、docs/spec。

## 3. 选择 defaults
问：偏好包目录名？默认 `defaults` → 业务仓 `.ai/defaults/`。
须含：`preferences.md`、`ai-coding.md`。

## 4A 新项目
问：名称与一句话目标、用户/问题、语言与栈、运行与部署、硬约束（性能/安全/兼容）。
按回答生成 AGENTS、memory、docs 骨架（空模块不建 components）。

## 4B 已有项目（首扫）
**范围**：源码主目录、README、现有 docs/AI 规则、包管理与锁文件、测试与 CI 配置、部署相关文件。
**忽略**：`node_modules`、`.git`、构建产物、大资源、密钥文件内容。
**深度**：识别核心模块边界、主数据流、启动/测试命令、既有约定；不要求读懂每一行。
**输出**：先列「模块清单 + 待确认」，再写 docs。

合并旧文档优先级：代码行为 > 测试 > 已确认文档 > 历史陈述 > 新生成。冲突标待确认。

## 5. 文件规则
| 类型 | 处理 |
|---|---|
| 普通 `.md`（defaults/workflow） | 复制到对应路径 |
| `*.template.md` | 分析后生成终稿 |
| 业务事实 | 只进 `docs/` |
| AGENTS | 提纲+加载策略，无业务正文 |

## 6. 目标结构
```
AGENTS.md
.ai/
  memory.md
  defaults/preferences.md
  defaults/ai-coding.md
  workflow/start.md
  workflow/sync.md
  workflow/end.md
  workflow/design-review.md
docs/
  index.md
  architecture/overview.md
  architecture/boundaries.md
  architecture/adr/          # 可空，有决策再写
  components/<module>/...    # 仅真实模块
  development/setup.md
  development/commands.md
  development/testing.md
  operations/...             # 有运维事实再写
```
无 skills、无 ai-profile、无 PROJECT_HISTORY。不建无意义空文件。

## 7. 生成要点
- **AGENTS**：填身份/边界/加载表；指向 `docs/index.md`；引用 defaults 与 workflow
- **docs**：遵循 `docs/spec.md`；components 与代码模块一一对应
- **memory**：五段+限高；首扫只放非显性约束与当前焦点
- **index.md**：任务 → 路径短表，支撑按需加载

## 8. 禁止
改业务逻辑、重构、加依赖、改架构、当修复 session 用。只建协作环境与知识地图。

## 9. 检查
- [ ] 模式与 defaults 已确认
- [ ] AGENTS 薄且无业务正文
- [ ] workflow + defaults 已就位
- [ ] docs 与真实模块对齐；index 可用
- [ ] memory 限高
- [ ] 旧知识已迁移或标待确认
- [ ] 未改业务代码

## 10. 报告
模式 / 项目判断摘要 / defaults / 生成与迁移列表 / 待确认 / 后续建议。
