# Bootstrap — Project

一次性使用。目标：把普通项目接入 agent.protocol v0.3，不改业务逻辑，不引入私有 AI 目录。

协议仓：https://github.com/AlloVince/agent.protocol

## 任务

1. 获取当前 agent.protocol 版本，阅读：
   - `templates/AGENTS.project.md`
   - `docs/spec.md`
   - `docs/engineering.md`
   - `docs/long-tasks.md`
2. 判断是新项目还是已有项目。
3. 已有项目先读取最小必要真实来源：
   - 当前 `AGENTS.md`（若有）
   - `README.md`
   - `owner/` 中与项目目标直接相关的文件（若有，只读）
   - package/runtime/lockfile/CI/部署配置
   - 主要源码目录、测试入口、正式 CLI/package scripts
   - 现有 docs 中与架构/运行直接相关的内容
4. 识别：项目目标、边界、真实技术栈、正式命令入口、已有内部基础设施、关键数据/模块边界。
5. 基于模板生成或更新根 `AGENTS.md`：
   - 保留项目特有约束
   - 删除模板中不适用的句子/占位
   - 不复制项目百科
   - 不创建 `.ai/`、preferences、memory、workflow
6. 处理 docs：
   - 只保留/新建对未来 Agent 有明确收益的文档
   - 不强制目录结构，不建空分类
   - 发现过期/重复文档时，优先修正或删除
7. `owner/`：
   - 不创建虚构的人类意图
   - 不修改已有内容
   - 如果缺少关键产品意图，只在报告中指出“建议人类补 owner”，不要替人写进去
8. 做一次工程入口审计，但不要在 bootstrap 阶段擅自大改业务：
   - 是否存在正式 build/test/dev 命令
   - 常规数据/运维是否有共享 CLI，还是散落临时脚本
   - 是否能发现项目已有内部库/能力，避免后续重复建设
   - 部署是否有明显遗漏的低成本生产默认项（例如静态压缩）；只报告，不趁机改业务
9. 输出报告：
   - 新/旧项目判断
   - `AGENTS.md` 关键条款
   - 可复用基础设施清单
   - 正式 CLI/命令入口
   - docs 保留/删除/新增理由
   - 明显缺口与后续建议

## 禁止

- 因为 bootstrap 顺手重构业务代码
- 创建 `.ai/` 或任何新的私有 Agent 配置树
- 自动填写/改写 `owner/`
- 把所有旧文档机械搬进 docs
- 把临时脚本包装成“Agent 专用工具”而不进入正式操作面
