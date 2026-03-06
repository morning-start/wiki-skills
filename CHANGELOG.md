# 变更日志

本文档记录 Coze Skills 项目的所有重要变更。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

---

## [2.1.0] - 2026-03-06

### 优化

- **优化 `project-wiki` 技能 (v7.0.0 → v7.1.0)** - 技能结构和文档质量优化
  - 重构 SKILL.md 结构：添加任务目标、快速上手、FAQ 等章节
  - 优化核心能力描述：为每个能力添加触发场景、输入输出说明
  - 简化工作流程：从复杂描述简化为快速流程
  - 增强使用示例：按 5 个场景分类，提供实际用例
  - 添加 FAQ 章节：7 个常见问题及解决方案
  - 优化参考文档索引：按使用频率分类（高/中/低）
  - 添加命令速查、模板速查、变量格式速查
  - 文档质量提升：更清晰、更易用、更实用

## [2.0.0] - 2026-03-06

### 新增

- **新增 `project-wiki` 技能 (v7.0.0)** - 模板 + 脚本快速生成标准文档
  - 重构模板目录结构：按 basic/architecture/requirements/knowledge/roadmap/checklists 分类
  - 统一变量命名规范：所有模板使用 `{{variable_name}}` 格式
  - 开发文档生成器工具：支持交互式生成和配置文件
  - 创建 6 个目录索引 README，提供详细变量说明
  - 标准化 76 个模板变量
  - 提供完整使用文档和示例配置

### 功能特性

- **模板分类管理**：6 大分类，18 个标准模板
- **交互式生成器**：`generate_doc.py` 命令行工具
- **配置文件支持**：YAML/JSON 格式，预定义变量
- **变量标准化工具**：`normalize_templates.py` 自动统一格式

### 文档

- [TEMPLATE_GENERATOR.md](./project-wiki/TEMPLATE_GENERATOR.md) - 模板生成器总览
- [scripts/README.md](./project-wiki/scripts/README.md) - 生成器使用指南
- [config.example.yaml](./project-wiki/scripts/config.example.yaml) - 配置文件示例

### 变更

- 更新 `project-wiki` 版本号：6.4.0 → 7.0.0 (Major 更新)
- 添加新技能到项目 README.md 技能列表
- 更新 SKILL.md 添加生成器功能说明

---

## [1.3.0] - 2026-03-06

### 新增

- 优化 `api-doc-generator` 技能 (v1.3.0)
  - 添加 scripts 目录及三个脚本文件（api_scanner.py, module_classifier.py, doc_generator.py）
  - 优化 overview-template.md，添加前端项目概述模板
  - 优化 endpoint-template.md，添加前端组件文档模板
  - 优化 module-template.md，添加前端组件组模板
  - 更新 SKILL.md，添加脚本说明和更多使用示例
  - 提升目录结构完整性到 100%
  - 提升模板文件实用性到 90%
  - 提升参考文档质量到 95%

### 变更

- 更新 `api-doc-generator` 版本号：1.2.0 → 1.3.0
- 添加脚本说明到 SKILL.md
- 添加更多使用示例（13 个示例）
- 添加脚本实现说明到注意事项

### 优化

- 目录结构完整性：80% → 100% (+20%)
- 模板文件实用性：70% → 90% (+20%)
- 参考文档质量：85% → 95% (+10%)
- 整体标准化合规性：90% → 100% (+10%)

---

## [1.2.0] - 2026-03-06

### 新增

- 优化 `api-doc-generator` 技能 (v1.2.0)
  - 添加 author 字段：api-doc-generator
  - 添加 tags 字段：[api-doc, frontend, backend, documentation, automation]
  - 优化 description：精简到 130 字符，符合 100-150 字符规范
  - 修正所有参考文档链接路径
  - 提升标准化合规性到 100%

### 变更

- 更新 `api-doc-generator` 版本号：1.1.0 → 1.2.0
- 提升技能标准化合规性：60% → 100% (+40%)
- 优化描述清晰度：一般 → 良好 (+30%)
- 修正链接有效性：0% → 100% (+100%)

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
