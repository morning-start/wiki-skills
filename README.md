# Coze Skills

Coze Skills 集合 - 为 AI 助手设计的专业技能库。

## 功能特性

- **独立版本管理**：每个技能拥有独立的版本号，存储在 `SKILL.md` 中
- **自动化构建**：支持批量构建所有技能为 `.skill` 格式包
- **CI/CD 集成**：GitHub Actions 自动构建和发布
- **灵活发布**：支持 Git Tag 触发或手动触发发布

## 快速开始

### 安装依赖

```bash
uv sync
```

### 本地构建

```bash
# 构建所有技能
uv run build-skills --all
# 指定版本号
uv run build-skills --all --version 1.0.0
# 构建单个技能
uv run build-skills --skill skill-name
# 列出所有技能
uv run build-skills --list
```

### 发布新版本

```bash
# 1. 更新技能版本号（修改 SKILL.md）
vim skill-name/SKILL.md

# 2. 提交代码
git add .
git commit -m "feat: 更新技能"
git push origin master

# 3. 创建 Tag 触发发布
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

## 项目结构

```
├── skills/              # 技能目录（每个子目录为一个技能）
│   └── skill-name/
│       └── SKILL.md     # 技能元数据（包含版本号）
├── scripts/             # 构建脚本
│   ├── build_skills.py  # 技能打包工具
│   ├── bump_version.py  # 版本号更新工具
│   └── ...
├── .github/workflows/   # CI/CD 配置
└── docs/                # 项目文档
```

## 技能结构

每个技能目录需包含 `SKILL.md` 文件：

```yaml
---
name: skill-name
version: 1.0.0
description: 技能描述
---
# 技能文档
```

## 命令行工具

| 命令             | 说明         |
| ---------------- | ------------ |
| `build-skills`   | 构建技能包   |
| `bump-version`   | 更新版本号   |
| `detect-changes` | 检测技能变更 |
| `generate-notes` | 生成发布说明 |

## 技能列表

| 技能名称                                                    | 版本  | 描述                                                                                                                                        | 标签                                                   |
| ----------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| [project-wiki](./project-wiki/SKILL.md)                     | 7.1.0 | 智能项目知识助手，支持模板 + 脚本快速生成标准文档、文档流程管理和知识库查询                                                                 | documentation, templates, generator, knowledge-base    |
| [api-doc-generator](./api-doc-generator/SKILL.md)           | 1.3.0 | 自动生成 API 文档，支持 React/Vue/Angular/Svelte/Next.js/Nuxt.js 等前端框架和 Flask/FastAPI/Django/Express/NestJS/Spring Boot/Gin/Echo 等后端框架 | api-doc, frontend, backend, documentation, automation  |
| [design-pattern-advisor](./design-pattern-advisor/SKILL.md) | 1.1.0 | 智能设计模式顾问，提供设计模式识别、推荐、代码优化和架构审查能力                                                                            | design-pattern, architecture, code-review, refactoring |
| [requirements-doc-gen](./requirements-doc-gen/SKILL.md)     | 1.0.0 | 将粗糙业务描述转化为标准SRS/PRD文档，支持需求变更分析、多端需求管理与自主知识补全                                                              | requirements, srs, prd, documentation, automation     |
| [quality-ops-doc-gen](./quality-ops-doc-gen/SKILL.md)       | 1.0.0 | 生成和优化质量与运维类文档（测试策略、部署运维、安全合规），支持多端场景、自主知识补全与需求变更分析                                              | testing, deployment, operations, security, compliance  |

## 文档

- [CI/CD 使用指南](./.github/CICD.md) - 构建和发布流程
- [Agent 工作流指南](./AGENTS.md) - Agent 操作规范
