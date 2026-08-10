# Agent Protocol

Version: 0.2

用最少提示词，让 AI 在任意项目里像熟练工程师一样工作。

## 解决什么

- 每次新 session 从零调教
- 规范靠口口相传、经验随对话蒸发
- 上下文被无关文档撑爆
- 代码与文档逐渐不一致

## 怎么用

1. 把 `bootstrap/minimal.md` 或 `bootstrap/standard.md` 交给 AI（一次性）
2. AI 扫描项目、选择 defaults、生成 `AGENTS.md` / `.ai/` / `docs/`
3. 之后每个 session 只让 AI 读 `AGENTS.md`，其余按需加载
4. 任务结束按规模执行 `.ai/workflow/end.md`

初始化完成后，不再需要 bootstrap 提示词。

## 结构（与业务仓一致）

```
project/
├── AGENTS.md                 # AI 入口：提纲与加载策略（无业务正文）
├── .ai/
│   ├── memory.md             # 短记忆（限高）
│   ├── defaults/             # 可替换偏好包（默认 defaults）
│   │   ├── preferences.md    # 工程/工具链/模型等偏好
│   │   └── ai-coding.md      # AI 编码行为
│   └── workflow/
│       ├── start.md
│       ├── sync.md
│       ├── end.md
│       └── design-review.md
└── docs/                     # 全部项目事实
    ├── index.md
    ├── architecture/
    ├── components/<module>/  # 按模块，按需加载
    ├── development/
    └── operations/
```

- `*.md`：可直接复制到业务仓
- `*.template.md`：按项目生成后去掉 `.template`

## 职责划分

| 位置 | 放什么 | 不放什么 |
|---|---|---|
| AGENTS.md | 导航、加载表、变更分级、禁止项 | 业务细节、模块说明书 |
| docs/ | 可验证的项目事实 | 工程哲学、会话临时状态 |
| defaults/ | 跨项目偏好（哲学也是偏好） | 项目特有业务 |
| memory.md | 代码/docs 说不清的雷区与焦点 | 架构复述、流水账 |
| workflow/ | 开工/同步/收工/架构自检 | 业务内容 |

冲突时：`代码 > 测试 > ADR/决策 > docs > memory`

## Profile

| | minimal | standard | full（未做） |
|---|---|---|---|
| AGENTS + defaults + memory | ✓ | ✓ | ✓ |
| workflow | — | ✓ | ✓ |
| docs 全套 | 精简 | ✓ | ✓ |
| skills | — | — | ✓ |

bootstrap 时询问使用哪个 defaults 目录，默认 `defaults`。

## 设计原则

1. **一次接入，长期自持**：约束在 AGENTS/workflow/docs，不依赖重复贴长提示词
2. **按需加载**：components 按模块切开；改谁读谁
3. **简约紧凑**：给 AI 的文档短、密、少空行
4. **规模门闩**：微/小/中/大任务匹配不同 end/sync/design-review 深度
5. **社区习惯**：AGENTS.md 入口、docs/、ADR、SemVer、Conventional Commits、main 主干

## 本仓文件

| 文件 | 给谁 |
|---|---|
| README.md | 人 |
| AGENTS.md | 维护本协议的 AI |
| AGENTS.template.md | 生成业务仓 AGENTS |
| .ai/** | 复制或生成到业务仓 |
| docs/spec.md | docs 写法规范（bootstrap 与生成时遵循） |
| bootstrap/* | 一次性接入剧本 |

## 技术偏好（写在 defaults，可整包替换）

默认偏向 Node（fnm/pnpm）与 Python（pyenv/uv）；main 主干；一次一功能；文档可用强模型、编码可用性价比模型。详见 `.ai/defaults/preferences.md`。
