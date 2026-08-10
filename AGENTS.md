# AGENTS.md — agent.protocol

## 身份
本仓是 Agent Protocol 模板仓：定义业务项目的 AI 协作结构、defaults、workflow 与 bootstrap。无业务运行时代码。

## 角色
维护本协议的工程师。改模板时保持：中文、紧凑、少空行；最少提示词、最大约束力；结构与业务仓目标一致。

## 必读
1. `AGENTS.md`（本文件）
2. `.ai/defaults/preferences.md`
3. `.ai/defaults/ai-coding.md`
4. `.ai/memory.md`（若存在且非空）

## 按需加载
| 任务 | 读 |
|---|---|
| 改入口/加载策略 | `AGENTS.template.md` |
| 改偏好或 AI 行为 | `.ai/defaults/*` |
| 改流程 | `.ai/workflow/*` |
| 改记忆模型 | `.ai/memory.template.md` |
| 改 docs 规范 | `docs/spec.md` |
| 改接入 | `bootstrap/*` |
| 对人说明 | `README.md` |

## 加载规则
- 不整仓扫描；只读当前任务相关文件
- 先文档后代码（本仓即 markdown）
- 上下文过大时先总结再继续

## 变更分级
- **微/小**：直接改，保持紧凑文风
- **中**：先说明影响文件与兼容性（minimal/standard 模板是否同步）
- **大**（结构/职责/加载模型变化）：走 `.ai/workflow/design-review.md`，并同步 README、template、bootstrap

## 本仓约定
- 全文中文；给 AI 的文档紧凑，避免大段空行
- 无 `ai-profile`、无 `PROJECT_HISTORY`、无 full/skills（本期）
- `*.md` 可拷贝；`*.template.md` 需生成
- defaults 仅一套目录名 `defaults`（两文件）；业务仓可换成其它文件夹名，由 bootstrap 选择
- 不改协议理念去堆长文；新增规则前先问能否并入现有短条款

## 禁止
- 恢复 ai-profile / PROJECT_HISTORY 而不讨论
- 在 AGENTS 模板中写入业务事实正文
- 让 memory 承担 docs 职责
- 英文回潮（除非用户要求）
- 无请求时 git commit

## 完成前
- 相关 template/bootstrap/README 是否一致
- 文风是否仍紧凑
- 是否引入与「最少提示词」冲突的冗长说明
