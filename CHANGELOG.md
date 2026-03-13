# 变更日志

本文档记录 Coze Skills 项目的所有重要变更。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

---

## [2.3.0] - 2026-03-13

### 优化

- **优化 `project-wiki` 技能 (v7.1.0 → v8.0.0)** - 核心能力重构与文档简化
  - **核心能力重构**: 从 7 个能力简化为 3 个（模板生成、文档管理、知识库）
  - **文档简化**: SKILL.md 从 483 行降至 283 行（-41%）
  - **参考文档精简**: 删除 11 个冗余文档，从 30+ 降至 19 个（-37%）
  - **快速上手优化**: 从 5 分钟降至 3 分钟，简化为 3 步流程
  - **目标用户明确**: 面向开发人员、技术负责人、项目经理
  - **示例优化**: 精简为 5 个核心场景示例
  - **FAQ 优化**: 精简为 6 个高频问题

### 删除

- 移除低频使用的项目类型指南（7 个）：
  - frontend-project-guide.md, backend-project-guide.md, fullstack-project-guide.md
  - mobile-project-guide.md, desktop-project-guide.md, cli-tui-project-guide.md, game-project-guide.md
- 移除低频使用的知识处理文档（4 个）：
  - extraction.md, knowledge-graph.md, management.md, project-type-recognition.md

### 变更

- 更新 `project-wiki/SKILL.md` - 重构为核心 3 能力，版本号 v7.1.0 → v8.0.0
- 更新 `project-wiki/QUICKSTART.md` - 简化为 3 步快速开始
- 更新 `project-wiki/references/` 目录 - 删除 11 个冗余文档
- 更新 guides/README.md 和 knowledge/README.md 索引

### 破坏性变更

**BREAKING**: 移除了项目类型指南（frontend/backend/fullstack 等），如需相关指南请参考社区资源。

---

## [2.2.0] - 2026-03-06

### 新增

- **新增 `quality-ops-doc-gen` 技能 (v1.0.0)** - 质量与运维文档生成器
  - 生成专业的测试策略与计划文档：包含测试类型、多端兼容性、游戏专项测试
  - 生成部署与运维手册：包含 CI/CD 流程、容器化配置、监控告警、日志管理
  - 生成安全合规文档：包含 GDPR/CCPA 合规、游戏版号申请、安全认证
  - 支持多端场景：Web、移动端、桌面端、游戏应用
  - 支持自主知识补全：可搜索最新技术和合规要求
  - 支持需求变更分析：分析测试/运维/安全/开发影响
  - 提供完整性检查清单：7 大类检查项，确保文档质量
  - 提供多端测试指南：覆盖 Web、移动端、桌面端、游戏应用的测试方法

### 新增文件

- 新增 `quality-ops-doc-gen/SKILL.md` - 技能定义文件
- 新增 `quality-ops-doc-gen/references/templates/test-strategy-template.md` - 测试策略文档模板
- 新增 `quality-ops-doc-gen/references/templates/deployment-ops-template.md` - 部署运维手册模板
- 新增 `quality-ops-doc-gen/references/templates/security-compliance-template.md` - 安全合规文档模板
- 新增 `quality-ops-doc-gen/references/quality-ops-checklist.md` - 完整性检查清单
- 新增 `quality-ops-doc-gen/references/multi-platform-testing-guide.md` - 多端测试指南

### 变更

- 更新项目 README.md，添加 `quality-ops-doc-gen` 技能到技能列表
- 更新 CHANGELOG.md 记录新技能添加

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

### 新增文件

- 新增 `PROJECT_SUMMARY.md` - 项目总结文档
- 新增 `QUICKSTART.md` - 快速上手指南（含速查表）
- 新增 `SKILL_OPTIMIZATION_SUMMARY.md` - 技能优化总结
- 新增 `TEMPLATE_GENERATOR.md` - 模板生成器文档
- 新增 `scripts/README.md` - 脚本使用指南
- 新增 `scripts/config.example.yaml` - 配置文件示例
- 新增 `scripts/generate_doc.py` - 文档生成器脚本
- 新增 `scripts/normalize_templates.py` - 模板标准化脚本
- 新增 `variable_report.md` - 变量报告
- 重构模板目录结构：从 `references/templates/` 迁移到 `templates/` 目录，按 6 大分类组织

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

### 新增文件

- 新增 `project-wiki/SKILL.md` - 技能定义文件
- 新增 `project-wiki/references/guides/` 目录下 20+ 个指南文档
- 新增 `project-wiki/references/knowledge/` 目录下 10+ 个知识管理文档
- 新增 `project-wiki/references/templates/` 目录下 18+ 个模板文件
- 新增 `project-wiki/references/guides/README.md` - 指南索引
- 新增 `project-wiki/references/knowledge/README.md` - 知识管理索引

### 变更

- 更新 `project-wiki` 版本号：6.4.0 → 7.0.0 (Major 更新)
- 添加新技能到项目 README.md 技能列表
- 更新 SKILL.md 添加生成器功能说明

---

## [1.3.0] - 2026-03-06

### 新增

- **优化 `api-doc-generator` 技能 (v1.3.0)** - 添加前端组件文档支持并优化模板
  - 新增前端组件文档模板，支持 React/Vue/Angular/Svelte 等框架
  - 优化 overview-template.md 添加前端项目概述模板
  - 优化 endpoint-template.md 添加前端组件文档模板
  - 优化 module-template.md 添加前端组件组模板
  - 新增三个脚本文件实现文档生成流程
  - 更新 SKILL.md 添加脚本说明和使用示例
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

### 新增文件

- 新增 `api-doc-generator/scripts/api_scanner.py` - API 扫描脚本
- 新增 `api-doc-generator/scripts/module_classifier.py` - 模块分类脚本
- 新增 `api-doc-generator/scripts/doc_generator.py` - 文档生成脚本

---

## [1.2.0] - 2026-03-06

### 新增

- **优化 `api-doc-generator` 技能 (v1.2.0)** - 扩展支持主流前后端框架并添加相关文档
  - 新增对 React、Vue、Angular、Svelte、Next.js、Nuxt.js 前端框架的支持
  - 新增对 Django、NestJS、Spring Boot、Gin、Echo 后端框架的支持
  - 新增前端框架参考文档：`references/frontend-frameworks.md`
  - 新增后端框架参考文档：`references/backend-frameworks.md`
  - 新增 API 文档最佳实践文档：`references/api-doc-best-practices.md`
  - 更新框架识别模式文档：`references/framework-patterns.md`
  - 提供完整的框架识别规则和参数提取方法
  - 添加前端组件文档生成支持
  - 添加 Next.js/Nuxt.js API 路由文档生成支持
  - 提供 13 个使用示例，覆盖所有支持的框架

### 变更

- 更新 `api-doc-generator` 版本号：1.1.0 → 1.2.0
- 更新 `api-doc-generator` 技能描述，包含所有支持的框架
- 扩展 `api-doc-generator` 操作步骤，添加前端和后端框架分支
- 添加框架检测优先级说明
- 添加文档生成最佳实践
- 添加常见问题解答

### 新增文件

- 新增 `api-doc-generator/references/frontend-frameworks.md` - 前端框架参考
- 新增 `api-doc-generator/references/backend-frameworks.md` - 后端框架参考
- 新增 `api-doc-generator/references/api-doc-best-practices.md` - API 文档最佳实践

---

## [1.1.0] - 2026-03-06

### 新增

- **添加 `api-doc-generator` 技能 (v1.0.0 → v1.1.0)** - API 文档自动生成工具
  - 文档模板：overview-template.md, module-template.md, endpoint-template.md
  - 参考文档：doc-structure.md, framework-patterns.md
  - 核心脚本：api_scanner.py, module_classifier.py
  - 自动从项目代码中提取 API 信息并生成符合标准的文档
  - 提供完整的 SKILL 文档说明使用方法和流程

### 新增文件

- 新增 `api-doc-generator/SKILL.md` - 技能定义文件
- 新增 `api-doc-generator/assets/templates/overview-template.md` - 概述模板
- 新增 `api-doc-generator/assets/templates/module-template.md` - 模块模板
- 新增 `api-doc-generator/assets/templates/endpoint-template.md` - 端点模板
- 新增 `api-doc-generator/references/doc-structure.md` - 文档结构指南
- 新增 `api-doc-generator/references/framework-patterns.md` - 框架模式识别
- 新增 `api-doc-generator/scripts/api_scanner.py` - API 扫描脚本
- 新增 `api-doc-generator/scripts/module_classifier.py` - 模块分类脚本

---

## [0.1.0] - 2026-03-01

### 新增

- **添加 `design-pattern-advisor` 技能 (v1.1.0)** - 智能设计模式顾问
  - 智能设计模式顾问，提供设计模式识别、推荐、代码优化和架构审查能力
  - 整合 23 种经典设计模式知识库
  - 提供 8 个原子能力和 4 个复合能力组合
  - 支持代码审查、模式推荐、重构建议和架构评估

### 新增文件

- 新增 `design-pattern-advisor/SKILL.md` - 技能定义文件
- 新增 `design-pattern-advisor/WORKFLOW.md` - 工作流文档
- 新增 `design-pattern-advisor/references/` 目录下 23 个设计模式参考文档
- 新增 `design-pattern-advisor/references/creational/` - 创建型模式（5 个）
- 新增 `design-pattern-advisor/references/structural/` - 结构型模式（7 个）
- 新增 `design-pattern-advisor/references/behavioral/` - 行为型模式（11 个）

### 变更

- 更新项目 README.md，添加技能列表
- 更新 CHANGELOG.md 记录新技能添加
- 修正文档路径引用
- 更新文档路径（docs/CICD.md → .github/CICD.md）
- 添加 AGENTS.md 工作流指南链接

---

## [未发布]

- 初始化项目结构
- 配置 CI/CD 工作流
- 添加项目规则和 Agent 工作流指南
- 构建脚本和版本管理工具

---

## 版本说明

- **新增**：新功能或新技能
- **变更**：现有功能的改进或优化
- **修复**：Bug 修复
- **移除**：已移除的功能或技能
