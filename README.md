# my-skills

我的可复用 Agent Skills 集合，当前包含：

## migration-prd —— 迁移版 PRD 生成器

从遗留系统代码生成「迁移版 PRD」（六大章节），供 Spring Boot + Vue 等新框架重写使用。

- **适用场景**：旧系统（Spring+Struts+Hibernate+JSP 等）迁移到新框架，没有需求文档，需要从代码反推需求基线。
- **核心原则**：代码是事实源；PRD 必须「现状(AS-IS) → 目标(TO-BE)」双栏对照；每个功能标注 保留/优化/废弃；验收标准可测试。
- **方法论**：借鉴 openwiki（代码取证）、grill-me（苏格拉底式追问）、superpowers（结构化成文）。

### 目录结构

```
migration-prd/
├── SKILL.md                  # 五步工作流（取证→追问→数据对齐→成文→验证）+ 六大章节质量红线
└── assets/
    ├── prd-template.md       # 六大章节 PRD 模板（填空即用）
    └── grill-checklist.md    # 逐功能追问清单（28 问）
```

### 六大章节

1. 背景与目标
2. 功能需求
3. 数据与接口需求
4. 非功能需求
5. AS-IS → TO-BE 差异表（每个功能必须有 保留/优化/废弃 决策）
6. 验收标准（可测试，Given-When-Then）

### 安装与使用

把 `migration-prd/` 目录放入技能目录：

- **Claude Code**：`~/.claude/skills/migration-prd/`（Windows 为 `%USERPROFILE%\.claude\skills\`）
- **豆包 / 其他 agent**：用户技能目录（如 `.user_skills/`）

放好后重启会话，对 agent 说「用 migration-prd 生成迁移 PRD」即可触发。

### 依赖环境（建议搭配）

| 工具 | 用途 | 安装 |
|---|---|---|
| openwiki | 代码取证，生成模块级代码 Wiki | `npm i -g openwiki`（Node ≥ 22） |
| grill-me | 需求追问，消除歧义 | `npx skills add https://github.com/mattpocock/skills --skill grill-me` |
| superpowers | 结构化设计与执行计划 | Claude Code 插件市场安装 |
