# fullstack-rules

前后端全栈开发规范 Skill，为 AI 编程助手提供统一的代码规范和最佳实践。

## 特性

- **8 条核心铁律** — DRY、文件大小限制、模块边界、禁止 emoji 图标等
- **10 个反例速查** — 常见错误写法 vs 正确做法，一目了然
- **AI 行为准则** — 约束 AI 修改代码时的行为，防止盲目操作
- **10 个规范文档** — 注释、命名、Git、安全、测试、前后端等全覆盖
- **丰富的代码模板** — DAO、模型、路由、迁移、错误处理等即用模板

## 适用场景

- 全栈项目开发（Node.js + Vue 3 / React）
- 新项目初始化和架构设计
- 代码审查和质量检查
- AI 辅助编程时的规范约束

## 目录结构

```
fullstack-rules/
├── SKILL.md                          # 主文件：核心铁律 + AI 行为准则 + 反例速查
├── references/
│   ├── note.md                       # 注释规范（文件头/函数/行内/日志）
│   ├── naming-convention.md          # 命名规范（代码/文件/DB/权限/API/Git）
│   ├── git-patterns.md               # Git 规范（分支/提交/CR/版本号）
│   ├── security.md                   # 安全规范（XSS/SQL注入/CSRF/权限/环境变量）
│   ├── testing.md                    # 测试规范（Jest/Vitest/Playwright/覆盖率）
│   ├── new-project.md                # 新项目初始化流程
│   ├── frontend/
│   │   ├── main.md                   # 前端通用规范
│   │   └── web/vue.md                # Vue 3 专用规范
│   └── backend/
│       ├── main.md                   # 后端通用规范
│       └── nodejs/nodejs-fastify.md  # Fastify 代码模板
└── assets/
    └── project-template/kt/kx-lang/  # kt 项目模板
```

## 快速开始

### 安装

将 `fullstack-rules` 目录复制到你的项目的 `.claude/skills/` 或 `.agents/skills/` 目录下：

```bash
# 方式一：直接复制
cp -r fullstack-rules /path/to/your/project/.claude/skills/

# 方式二：作为 git submodule
git submodule add https://github.com/yijiu2025/well-skill.git .claude/skills/fullstack-rules
```

### 使用

AI 编程助手会在以下场景自动加载此 Skill：

- 用户进行全栈开发、创建新项目
- 编写前后端代码、设计 API 接口
- 进行代码审查、需要遵循团队开发规范

手动触发：在对话中输入 `/fullstack-rules`

## 核心规范速览

### 8 条核心铁律

| # | 铁律 | 说明 |
|---|------|------|
| 1 | DRY 原则 | 拒绝重复代码，合理抽取公共组件和工具函数 |
| 2 | 文件大小 ≤ 1000 行 | 接近 700 行主动拆分 |
| 3 | 一个文件 = 一个模块 | 组件 A 不内嵌组件 B 的 UI/逻辑 |
| 4 | UI 禁止 emoji 图标 | 用图标库或内联 SVG |
| 5 | 修改前先说明计划 | 不确定的业务逻辑先提问 |
| 6 | 每个函数写文档注释 | JSDoc/Docstring 格式 |
| 7 | 错误处理 | 不吞噬异常，捕获并记录日志 |
| 8 | 主动提交 git | Conventional Commits 格式 |

### 反例速查

| 场景 | ❌ 错误 | ✅ 正确 |
|------|--------|--------|
| API 请求 | 组件内直接调用 | 封装到 `src/api/` |
| 错误处理 | `catch { }` | `catch (e) { logger.error(e); throw e }` |
| 类型 | `any` | 具体类型 `ApiResult<User>` |
| SQL | `WHERE id = ${id}` | `WHERE id = ?` |
| 提交 | `git commit -m "fix bug"` | `git commit -m "fix(login): 修复空指针异常"` |

## 规范文档

| 文档 | 说明 |
|------|------|
| [注释规范](references/note.md) | 文件头注释、函数注释、行内注释、TODO 标记、控制台日志 |
| [命名规范](references/naming-convention.md) | 代码/文件/数据库/权限/API/Git 命名规则 |
| [Git 规范](references/git-patterns.md) | 分支模型、提交信息、PR 模板、版本号 |
| [安全规范](references/security.md) | 敏感信息、XSS/SQL注入/CSRF 防护、权限校验、环境变量管理 |
| [测试规范](references/testing.md) | 测试文件命名、Jest/Vitest/Playwright 模板、覆盖率阈值 |
| [前端规范](references/frontend/main.md) | 技术栈、组件开发、数据加载、API 响应格式 |
| [Vue 3 规范](references/frontend/web/vue.md) | 权限系统、组件架构、样式规范、TypeScript 配置 |
| [后端规范](references/backend/main.md) | 分层架构、统一响应格式、数据库规范 |
| [Fastify 模板](references/backend/nodejs/nodejs-fastify.md) | API 路由、DAO、模型、迁移、错误处理 |
| [新项目模板](references/new-project.md) | 从零创建新项目的初始化流程 |

## 技术栈

| 领域 | 技术选型 |
|------|----------|
| 后端运行时 | Node.js ESM |
| 后端框架 | Fastify v5 |
| ORM | Sequelize v6 + MySQL2 |
| 缓存 | Redis v5 (node-redis) |
| 前端框架 | Vue 3 + Vite + TypeScript |
| 状态管理 | Pinia |
| 测试 | Jest (后端) + Vitest (前端) + Playwright (E2E) |

## 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建你的分支 (`git checkout -b feature/amazing-feature`)
3. 提交你的修改 (`git commit -m 'feat: 添加某个特性'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 创建一个 Pull Request

## 版本历史

- **v1.1.0** (2026-07-20)
  - 新增 E2E 测试规范（Playwright）
  - 新增 CSRF 防护规范
  - 新增 AI 行为准则
  - 新增反例速查表（10个场景）
  - 新增版本号管理

- **v1.0.0** (2026-07-18)
  - 初始版本
  - 8 条核心铁律
  - 10 个规范文档
  - 丰富的代码模板

## 许可证

[MIT License](LICENSE)

## 致谢

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [Sequelize](https://sequelize.org/)
- [Fastify](https://www.fastify.io/)
- [Vue 3](https://vuejs.org/)
