# 更新日志

本文件记录 fullstack-rules 的所有重要变更。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [2.3.0] - 2026-09-05

### 新增

- **分层加载架构**：SKILL.md 瘦身为 129 行核心层，低频内容下沉 16 个按需 references（日常会话省 4-6k token）
- **端到端任务剧本**（workflows.md）：六大剧本——新增 API / 新增页面 / 对接外部 API / 修复 Bug / 代码审查 / 安全审查
- **事故复盘库**（pitfalls.md）：12 条真实生产事故（现象→根因→规则→防回归），含设备 ID 算法漂移、路由重复注册、401 刷新死锁、SSO 主题竞态等
- **技能编排规范**（orchestration.md）：11 场景决策表，可调度安全测试 / UI 设计 / Redis 等环境内其他专项技能，含降级容错
- **代码检查工具箱**（toolbox.md）：检查金字塔 + 场景化命令矩阵 + 提交前最终清单
- **doctor.mjs 自检脚本**：链接可达性 / 禁用模式 / 行数上限 / 必需文件的机器校验
- **双语仓库文档**：README.md（English）+ README.zh-CN.md（简体中文）
- **MIT LICENSE**

### 修复

- 路径全面对齐：`src/db|redis|auth` → `src/framework/*`（7 个 references + AGENTS.md/CLAUDE.md 同步）
- 模板矛盾：DAO `sequelize.models` → `getModel`（对齐铁律）；`reply.result.success` 签名对齐真实装饰器
- 删除虚构 Jest 配置项 `setupFilesAfterSetup`；testMatch 对齐仓库实际
- 断链修复（vue.md 层级、security.md 链接）；naming-convention 破损表格重写；new-project 步骤编号修正
- assets 移除嵌套 .git 与重复 README，保留 SPEC.md + example.kx

## [1.1.1] - 2026-07-21

### 修复

- **naming-convention.md**：修正 Composables 文件命名规则冲突（hooks/ 目录用 camelCase，其他工具文件用 kebab-case），新增例外说明
- **nodejs-fastify.md**：模型模板 `paranoid: true` → `paranoid: false`，与自定义 `delete_version` 软删除模式保持一致
- **note.md**：移除错误处理反例（不属于注释规范范畴，已在 security.md 和 nodejs-fastify.md 中覆盖）

## [1.1.0] - 2026-07-20

### 新增

- **AI 行为准则**：约束 AI 修改代码时的行为（先读后改、不改无关代码、不确定先问等）
- **反例速查表**：10 个常见场景的正反例对照（API 请求、错误处理、类型、SQL、提交等）
- **E2E 测试规范**：Playwright 测试模板、原则、运行命令
- **CSRF 防护规范**：原理、4 种防护措施、Fastify 配置、前端配合
- **环境变量管理**：文件层级、命名规范、维护规则
- **版本号管理**：SKILL.md frontmatter 中添加 version 字段

### 改进

- **SKILL.md**：新增"AI 行为准则"和"反例速查"章节，提升可执行性
- **note.md**：新增注释反例（4处）和错误处理反例（4处）
- **naming-convention.md**：新增命名反例段（JS变量、常量、文件命名）
- **security.md**：章节从九章扩展为十章，新增 CSRF 和环境变量管理
- **testing.md**：章节从五章扩展为六章，新增 E2E 测试
- **git-patterns.md**：新增提交信息反例（无意义信息、多改动合并等）
- **frontend/main.md**：新增组件反例（3处）和数据加载反例（2处）
- **backend/main.md**：从 31 行扩充为完整规范（分层架构/响应格式/数据库规范）
- **vue.md**：新增 TypeScript 严格模式配置表
- **AGENTS.md**：精简重复内容，添加引用链接

### 评分提升

- 综合评分从 7.18 提升至 8.70（+1.52）
- 反例覆盖从 0 处增至 24 处
- 文件总量从 2363 行优化至 1847 行（-22%）

## [1.0.0] - 2026-07-18

### 新增

- **核心铁律**：8 条基本规则（DRY、文件大小、模块边界、禁止 emoji 等）
- **模块边界规则**：职责单一、不内嵌其他模块、状态归属、跨模块通信、禁止反向依赖
- **图标使用规范**：禁止 UI 使用 emoji、优先使用 lucide-vue-next
- **修复问题原则**：先分析再修改，禁止盲目尝试
- **输出格式要求**：思考过程、代码输出、依赖说明、修改后验证

### 规范文档

- **note.md**：注释规范（文件头/函数/行内/日志）
- **naming-convention.md**：命名规范（代码/文件/DB/权限/API/Git）
- **git-patterns.md**：Git 规范（分支/提交/CR/版本号）
- **security.md**：安全规范（XSS/SQL注入/权限/认证）
- **testing.md**：测试规范（Jest/Vitest/覆盖率）
- **frontend/main.md**：前端通用规范
- **frontend/web/vue.md**：Vue 3 专用规范
- **backend/main.md**：后端通用规范
- **backend/nodejs/nodejs-fastify.md**：Fastify 代码模板
- **new-project.md**：新项目初始化流程

### 代码模板

- API 路由模板
- DAO 模板
- 模型模板
- 迁移文件模板
- 序列化函数模板
- Loader 注册模板
