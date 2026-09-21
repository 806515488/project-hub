<!-- project-hub v5 -->

# 项目规范

优先级：仓库内文档 > 工具本地记忆 > AI 自由发挥。与规则冲突的 AI 默认习惯一律不生效。

## 工具链与命令

- 构建/运行/测试：<从项目配置文件归纳，写可直接执行的命令>

## 代码组织

- <目录怎么用、新文件放哪、命名规则>
- 样板示例（新代码模仿这段）：

```<语言>
<从现有代码中挑一段最有代表性的贴进来>
```

## 提交规范

- 格式：`[<工具名>] <改动摘要>`，如 `[claude] 修复登录超时`
- 一次任务一个 commit，换工具前先把上个工具的改动提交

## 落文档纪律

1. 文档只沉淀结果：一行结论 + 涉及文件路径 + 当前状态。不写过程叙述。
2. 坑只记「会再踩的」，一行一条：`现象：解法（日期）`
3. 跟某主题绑定的坑记入该主题文档的坑区；通用坑记入本文件坑区。

## 坑

<!-- 通用环境/工具坑，一行一条 -->

## 信息落点（记录任何信息前，先对号入座）

| 要记的信息 | 写到哪 |
|---|---|
| 约定、命令、环境事实 | docs/conventions.md |
| 进度、计划、挂起问题 | docs/status.md |
| 主题知识、领域笔记 | docs/notes/ 对应文件 |
| 踩过的坑 | 对应文档的坑区，一行一条 |
| 入口文件（CLAUDE.md / AGENTS.md 等） | ✗ 禁止写入正文，只做指向 |
| 新建根目录散文件（XX.md） | ✗ 禁止，一律进 docs/ 体系 |

## 入口文件标准（唯一权威源；缺失或被改动时按此补齐，内容一律 3 行以内、只做指向）

一句话正文 `POINT` = `Read PROJECT.md first and follow its index. Repo docs > your local memory > your defaults.`

| 入口文件 | 内容 |
|---|---|
| `AGENTS.md`、`GEMINI.md`、`.clinerules` | POINT |
| `CLAUDE.md` | `@PROJECT.md` |
| `.github/copilot-instructions.md` | `Read PROJECT.md first and follow its index. Repo docs take precedence over your defaults.` |
| `.cursor/rules/project-hub.mdc` | frontmatter + POINT，完整格式见下 |
| `.windsurf/rules/project-hub.md` | frontmatter + POINT，完整格式见下 |

`.cursor/rules/project-hub.mdc`：

```markdown
---
description: project-hub entry
globs:
alwaysApply: true
---
<POINT>
```

`.windsurf/rules/project-hub.md`：

```markdown
---
trigger: always_on
---
<POINT>
```

小众工具（需要时按相同原则补建）：Kilo Code `.kilocoderules`、Trae `.trae/rules/project-hub.md`（内容 = POINT）；Aider `CONVENTIONS.md`（内容 = POINT，且需在 `.aider.conf.yml` 配 `read: CONVENTIONS.md` 才生效）。
