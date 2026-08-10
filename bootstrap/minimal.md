# Agent Protocol Bootstrap Minimal

版本: 1.0


# 角色定义


你正在帮助一个项目接入：

Agent Protocol Minimal Profile


官方协议仓库：

https://github.com/AlloVince/agent.protocol


你的目标：

建立一个最小但有效的 AI 协作环境。


不要创建复杂流程。

不要增加不必要文档。

优先保持简单。



---

# 1. 初始化目标


初始化完成后：

AI Agent 应该能够理解：


- 项目是什么；
- 如何运行；
- 使用什么技术；
- 修改代码时遵循什么规则。



Minimal Profile 的目标：

减少重复提示。

避免 AI 犯基础错误。



---

# 2. 判断项目类型


确认：


## 新项目


没有代码和文档。


需要通过提问建立项目基础信息。



## 已有项目


已有代码或文档。


需要分析现状。



如果无法判断：

询问用户。



---

# 3. 获取协议


获取：

https://github.com/AlloVince/agent.protocol


读取：

- AGENTS.template.md
- .ai/defaults/
相关文件。



---

# 4. 新项目初始化


如果是新项目：

询问必要信息：


## 项目目标

- 项目名称；
- 项目用途；
- 核心功能。


## 技术方案

- 编程语言；
- Framework；
- Runtime；
- 数据存储。



## 开发方式

- 本地运行方式；
- 测试方式；
- 部署方式。



不要询问暂时不会影响开发的问题。



---

# 5. 已有项目初始化


如果是已有项目：


检查：


- README.md；
- package.json；
- pyproject.toml；
- requirements文件；
- 项目目录；
- 已有文档。


理解：

- 项目用途；
- 技术栈；
- 运行方式；
- 核心模块。



不要修改代码。



---

# 6. 文件处理规则


## 普通 Markdown


格式：

*.md


处理：

直接复制。



例如：

.ai/defaults/engineering-defaults.md


---

## 模板文件


格式：

*.template.md


处理：

读取模板。

根据项目生成最终文件。


例如：

AGENTS.template.md
↓
AGENTS.md



---

# 7. Minimal 文件结构


创建：


AGENTS.md
.ai/
├── ai-profile.md
├── memory.md
└── defaults/
├── engineering-defaults.md

└── ai-coding-defaults.md


---

# 8. AGENTS.md


根据：

AGENTS.template.md


生成。


必须包含：


- 项目简介；
- AI入口规则；
- 文档加载方式；
- 基本开发约束。



不要复制大量通用规则。


通用规则来自：

.ai/defaults/



---

# 9. ai-profile.md


记录：


- 项目名称；
- 项目类型；
- 技术栈；
- 开发环境；
- 常用命令；
- 重要限制。



保持简洁。


---

# 10. memory.md


初始化为空或少量内容。


只记录：


- 重要项目事实；
- 不明显的约束；
- 后续 AI 必须知道的信息。



不要记录：

- 临时任务；
- 最近修改；
- 可以通过代码获得的信息。



---

# 11. 初始化限制


禁止：


- 修改业务代码；
- 自动重构；
- 添加依赖；
- 修改架构。



初始化只创建：

AI协作基础。



---

# 12. 完成检查


确认：


□ AGENTS.md 已生成

□ .ai 已创建

□ 默认规则已复制

□ 项目信息已记录

□ 没有修改业务代码



---

# 13. 输出报告


输出：


初始化完成
项目类型：
生成文件：
已确认信息：
待补充信息：
建议下一步：