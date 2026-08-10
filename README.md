# Agent Protocol Design Session Context

Version: 0.1

## 1. 项目目标

正在设计一个名为 `agent.protocol` 的 AI Agent 开发规范仓库。

目标：

通过一套标准化的目录结构、文档规范和 workflow，让 AI Agent 在进入任何项目时：

- 快速理解项目；
- 遵循统一工程规范；
- 继承长期积累的工程经验；
- 避免重复提示；
- 保持代码、文档、知识同步；
- 支持长期演进的软件开发。


核心理念：

> 通过优秀的架构设计和工程经验沉淀，让小团队拥有大型团队多年实践积累的系统能力。


---

# 2. 核心设计原则


## 2.1 文档驱动开发

AI 不应该依赖每次人工重复说明。

项目应该通过文档保存：

- 工程规则；
- 架构知识；
- 历史经验；
- 开发流程；
- 技术约束。


新的 AI Session：

通过阅读入口文档恢复上下文。


---

## 2.2 agent.protocol 与业务项目目录严格对应

原则：

agent.protocol 仓库中的结构：

必须对应业务代码仓库中的目标结构。


原因：

- 最简单；
- bootstrap 脚本容易处理；
- Agent容易理解。


部分目录可以因为项目规模不存在。

由 bootstrap 决定：

- minimal
- standard
- full

agent.protocol 中的文件

如果以 .md 结尾，代表这是一个可复制的文件, 如 .ai/defauts/engineering-defaults.md
如果以 .template.md 代表这是一个模板文件，需要 Agent 根据业务仓库的实际情况读取模板生成 如 AGENTS.template.md 在目标业务仓库中生成 AGENTS.md


---

# 3. 目标项目结构


最终业务项目结构：


```
project/

├── AGENTS.md
├── README.md
├── PROJECT_HISTORY.md

├── .ai/

│   ├── memory.md
│   ├── ai-profile.md
│
│   ├── defaults/
│   │   ├── engineering-defaults.md
│   │   └── ai-coding-defaults.md
│   │
│   ├── workflow/
│   │   ├── start.md
│   │   ├── sync.md
│   │   ├── end.md
│   │   └── design-review.md
│   │
│   └── skills/

├── docs/

│   ├── architecture/
│   │
│   ├── components/
│   │
│   ├── development/
│   │
│   └── operations/

```


---

# 4. 文件职责


## AGENTS.md

定位：

项目 AI 总入口。


负责：

- 项目规则；
- 文档加载规则；
- AI 工作方式；
- 项目边界。


每个 Session 首先读取。


状态：

已设计 template。

文件：

```
AGENTS.template.md
```


---

# 5. .ai/defaults


## engineering-defaults.md


定位：

工程哲学。


内容包括：

- 复杂度管理；
- 渐进式架构；
- 能力沉淀；
- 人类可理解代码；
- 组件设计；
- 工程责任；
- 依赖管理；
- Node/Python环境；
- 语义化发布；
- 可靠性；
- AI时代工程原则。


状态：

已完成 v1。


---

## ai-coding-defaults.md


定位：

约束 AI 编码行为。


核心：

AI 是维护已有代码库的高级工程师。


规则：

- 先理解后编码；
- 最小修改；
- 遵循已有模式；
- 控制上下文；
- 不提前抽象；
- 不偷偷改架构；
- 测试意识；
- 文档同步意识。


状态：

已完成 v1。


---

# 6. .ai/workflow


## start.md

定位：

Session启动流程。


目标：

让 AI 像已经加入团队一年一样开始工作。


流程：

```
AGENTS.md

↓

memory.md

↓

defaults

↓

相关docs

↓

相关代码
```


特点：

按需加载。

避免扫描整个仓库。


已增加：

Context Budget。


---

## design-review.md


定位：

架构变化审查。


目的：

防止 AI 过度设计。


触发：

- 新架构；
- 新基础设施；
- 模块边界变化；
- 核心数据模型变化；
- 技术栈重大变化。


不触发：

- bug修复；
- 简单feature；
- 小范围重构。


核心理念：

> 不因为未来可能需要，而增加今天不需要的复杂度。


---

## sync.md


定位：

代码和知识同步。


解决：

- AI写代码；
- 人写代码；
- 外部merge。


原则：

代码是真实状态。

如果冲突：

代码 > 测试 > 决策 > 文档 > memory。


---

## end.md


定位：

Session结束交接。


负责：

- 总结修改；
- 检查文档影响；
- 更新memory；
- 记录未完成事项。


不负责：

自动git commit。


---

# 7. ai-profile.md

当前未完成。


定位：

项目运行环境配置。


不属于：

工程理念。

不属于：

AI行为规则。


应该记录：

- 项目技术栈；
- Node/Python版本；
- 框架；
- 数据库；
- 基础设施；
- 开发命令；
- 项目约束；
- AI协作偏好。


不要记录：

- 工程哲学；
- workflow；
- 历史经验。


---

# 8. memory.md

当前未设计。


这是下一步重点。


目标：

保存：

未来AI需要知道，但代码本身无法表达的信息。


需要解决：

- 防止无限增长；
- 防止历史污染；
- 控制token成本；
- 支持长期维护。


预计需要设计：

- Active Memory
- Stable Knowledge
- Historical Memory
- Confidence等级
- 淘汰机制


---

# 9. Bootstrap设计


Bootstrap 不放入 agent.protocol。


原因：

bootstrap 是初始化工具，不属于项目结构。


计划：

三个版本：

```
minimal

standard

full
```


作用：

读取 agent.protocol 模板。

分析已有项目。

生成：

- AGENTS.md
- .ai
- docs


同时支持：

新项目。

已有 AI 文档项目迁移。


---

# 10. 技术默认值


当前确认：


Node:

- fnm
- pnpm
- 最新LTS


Python:

- pyenv
- uv
- venv
- 最新稳定版本


发布：

- Semantic Versioning
- Conventional Commits


开发模式：

- git main 主干
- 一次完成一个功能


AI：

- DeepSeek作为主要编码模型
- 强模型负责架构/设计
- 性价比模型负责实现


---

# 11. 当前待继续设计


优先级：


## 1. 完成 ai-profile.md


## 2. 设计 memory.md

重点：

长期知识管理。

## 3. 设计 bootstrap



## 4. 完善 docs目录规范


明确：

architecture

components

development

operations


各自包含什么。


## 5. 设计 skills目录

需要评估：

- 是否需要skill；
- skill边界；
- 引入成本；
- 风险。


---

# 12. 当前核心判断


这个协议不是：

“AI提示词集合”。


它更接近：

> AI时代的软件工程操作系统。


核心闭环：


```
AGENTS.md

↓

读取规则


.ai/defaults

↓

工程基因


.ai/memory

↓

团队经验


.ai/workflow

↓

工作流程


docs

↓

项目知识


代码

↓

真实系统
```


目标：

让任何新 AI Session：

像一个已经加入团队一年以上的工程师一样工作。