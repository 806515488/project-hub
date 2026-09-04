# 新项目模式（bootstrap）

适用：根目录无 PROJECT.md 且无实质文档的项目。产出整套维护架构。

## 执行顺序

### 1. 建目录骨架

```
docs/
├── status.md          ← 当前进度 / 下一步 / 挂起问题（滚动更新）
├── conventions.md     ← 规范：约定、落文档纪律、坑区
└── notes/             ← 知识/主题文档，一主题一文件（按项目性质命名）
```

notes/ 下的文件按项目实际主题创建，不预建空文件。

### 2. 套模板生成文件

从 `references/templates/` 取模板填充：

- `PROJECT.template.md` → 根目录 `PROJECT.md`（索引条目必须带「触发条件」，即什么任务读什么文件）
- `status.template.md` → `docs/status.md`
- `conventions.template.md` → `docs/conventions.md`

### 3. 生成全部入口文件

格式权威源：`references/templates/conventions.template.md` 的「入口文件标准」区（AGENTS.md、CLAUDE.md、GEMINI.md、.cursor/rules/project-hub.mdc、.github/copilot-instructions.md、.windsurf/rules/project-hub.md、.clinerules），照其逐一生成。

规则：

- 已存在的入口文件**不覆盖**，将其内容改写为指向 PROJECT.md（原内容如仍有价值，归并进 docs/ 对应文档）
- 小众工具默认不建，用户提及时按 conventions 模板「入口文件标准」区备注补建
- 用户已明确不用的工具可跳过，问一句即可

### 4. .gitignore 安全检查

- 确认排除各 AI 工具的本地配置与凭据：`.claude/settings.local.json` 等 local 类文件、各工具凭据/缓存目录
- 检查待提交内容中有无密钥（token、密码、`.env` 等），有则加入 .gitignore 并提醒用户

### 5. 填充真实内容

- status.md：扫描项目现状填写「当前状态」
- conventions.md：从 pom.xml / package.json / 现有代码风格归纳工具链与约定，样板示例从现有代码中挑一段贴入

### 6. 收尾

按 SKILL.md「收尾检查」执行，提醒用户 commit。
