# 变更日志

本文档记录 Coze Skills 项目的所有重要变更。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

---

## [1.1.0] - 2026-03-06

### 新增

- 添加 `api-doc-generator` 技能 (v1.1.0)
  - 扩展支持主流前端框架：React、Vue、Angular、Svelte、Next.js、Nuxt.js
  - 扩展支持主流后端框架：Django、NestJS、Spring Boot、Gin、Echo
  - 新增前端框架参考文档：`references/frontend-frameworks.md`
  - 新增后端框架参考文档：`references/backend-frameworks.md`
  - 新增 API 文档最佳实践文档：`references/api-doc-best-practices.md`
  - 更新框架识别模式文档：`references/framework-patterns.md`
  - 提供完整的框架识别规则和参数提取方法
  - 添加前端组件文档生成支持
  - 添加 Next.js/Nuxt.js API 路由文档生成支持
  - 提供 13 个使用示例，覆盖所有支持的框架

### 变更

- 更新 `api-doc-generator` 版本号：1.0.0 → 1.1.0
- 更新 `api-doc-generator` 技能描述，包含所有支持的框架
- 扩展 `api-doc-generator` 操作步骤，添加前端和后端框架分支
- 添加框架检测优先级说明
- 添加文档生成最佳实践
- 添加常见问题解答

---

## [0.1.0] - 2026-03-01

### 新增

- 添加 `design-pattern-advisor` 技能 (v1.1.0)
  - 智能设计模式顾问，提供设计模式识别、推荐、代码优化和架构审查能力
  - 整合23种经典设计模式知识库
  - 提供8个原子能力和4个复合能力组合
  - 支持代码审查、模式推荐、重构建议和架构评估

### 变更

- 更新项目 README.md，添加技能列表
- 更新文档路径（docs/CICD.md → .github/CICD.md）
- 添加 AGENTS.md 工作流指南链接

---

## [未发布]

---

## 版本说明

- **新增**：新功能或新技能
- **变更**：现有功能的改进或优化
- **修复**：Bug 修复
- **移除**：已移除的功能或技能
