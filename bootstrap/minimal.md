# Bootstrap · Minimal

一次性接入。完成后业务仓靠 AGENTS/docs/defaults 自持，不再需要本文件。
协议：https://github.com/AlloVince/agent.protocol
原则：最小可用；不改业务代码；中文；紧凑；不编造。

## 目标
生成后 AI 能知道：项目是什么、怎么跑、技术偏好、改代码的基本规矩。

## 1. 模式
判断：新项目（几乎无代码）| 已有项目。不确定则问。

## 2. 拉取协议
获取协议仓最新内容，读：`AGENTS.template.md`、`.ai/defaults/`、`.ai/memory.template.md`、`docs/spec.md`。

## 3. 选择 defaults
询问：使用哪个偏好目录？默认 `defaults`（复制为业务仓 `.ai/defaults/`）。
用户指定其它文件夹名则从其包复制（须含 preferences + ai-coding 两文件等价物）。

## 4. 收集/分析
**新项目**：问名称、一句话目标、语言/框架、怎么跑/测。不问暂时不影响开发的问题。
**已有项目**：读 README、包配置、目录、已有 AI/文档。理解用途、栈、启动方式、核心模块。不改代码。

## 5. 生成结构
```
AGENTS.md                 # 由 template 生成
.ai/
  memory.md               # 由 template 生成，尽量短
  defaults/
    preferences.md
    ai-coding.md
docs/
  architecture/overview.md   # 极简
  development/commands.md    # 必有
```
无则不建空目录。不生成 workflow（minimal 无）。不生成 ai-profile、PROJECT_HISTORY。

## 6. 文件规则
- 协议内普通 `.md`（defaults 等）：复制
- `*.template.md`：按项目填空生成，去 `.template`
- AGENTS：只做提纲与加载表，**不写业务正文**；业务在 docs
- 遵循 `docs/spec.md` 的 minimal 裁剪

## 7. AGENTS 填写
身份四行 + 边界 + 加载表指向已有 docs。通用规则引用 `.ai/defaults/`，不复制长文。

## 8. memory
按五段模板；能空则空。只写非显而易见约束。标 Confirmed/Assumed。

## 9. 禁止
改业务逻辑、重构、加依赖、改架构、自动修业务 bug。只建 AI 协作骨架与 docs 事实。

## 10. 检查
- [ ] AGENTS.md 已生成且无业务说明书
- [ ] defaults 两文件已就位
- [ ] memory 限高
- [ ] docs 为真实信息，待确认已标记
- [ ] 未改业务代码

## 11. 报告
模式 / 所选 defaults / 生成文件 / 已确认 / 待补充 / 建议下一步（如升 standard）。
