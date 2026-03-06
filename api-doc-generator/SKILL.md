---
name: api-doc-generator
version: 1.1.0
description: 自动分析项目代码并生成符合标准格式的API文档；支持React/Vue/Angular/Svelte/Next.js/Nuxt.js等前端框架；支持Flask/FastAPI/Django/Express/NestJS/Spring Boot/Gin/Echo等后端框架；自动划分功能模块和层级结构；生成包含概述、认证、端点详情、错误处理等完整章节的文档
dependency:
  python:
    - ast
---

# API 文档自动生成器

## 任务目标

- 本 Skill 用于：从项目代码中自动提取API信息并生成完整的API文档
- 能力包含：代码扫描、路由识别、模块划分、文档结构化、内容填充
- 触发条件：用户要求"生成API文档"、"分析项目API"、"编写接口文档"等

## 前置准备

### 依赖说明

本 Skill 仅使用 Python 标准库（ast, re, json, pathlib等），无需额外安装依赖。

### 非标准文件/文件夹准备

无需前置创建，输出目录将在文档生成时自动创建。

## 操作步骤

### 标准流程

1. **步骤1：扫描项目API**
   - 调用 `scripts/api_scanner.py` 扫描项目代码
   - 参数：
     - `--project-dir`: 项目根目录（必需）
     - `--framework`: 框架类型（auto/flask/fastapi/express/django/nestjs/spring/gin/echo/react/vue/angular/svelte/nextjs/nuxtjs，默认auto）
     - `--output`: 输出JSON文件路径（默认api_scan_result.json）
   - 输出：包含所有API端点信息的JSON文件

2. **步骤2：模块划分与层级分析**
   - 调用 `scripts/module_classifier.py` 分析API结构
   - 参数：
     - `--input`: 上一步输出的JSON文件路径
     - `--output`: 输出JSON文件路径（默认api_modules.json）
   - 输出：带模块分组和层级信息的API清单

3. **步骤3：生成文档结构**
   - 在项目根目录下创建 `api/` 文件夹
   - 根据 `references/doc-structure.md` 中的规范创建文档框架：
     - `api/overview.md` - API概述
     - `api/authentication.md` - 认证方式
     - `api/base-info.md` - 基础信息
     - `api/endpoints/` - 端点详情（按模块组织）
     - `api/error-handling.md` - 错误处理
     - `api/rate-limiting.md` - 速率限制
     - `api/changelog.md` - 变更日志
     - `api/support.md` - 支持与反馈

4. **步骤4：填充文档内容**
   - 根据模块划分结果，为每个模块创建独立的端点文档
   - 使用 `assets/templates/` 中的模板填充内容
   - 补充说明文字、示例代码、注意事项等

### 可选分支

#### 后端框架分支

- **当项目使用Flask框架**：在步骤1中明确指定 `--framework flask` 以提高识别准确率
- **当项目使用FastAPI框架**：在步骤1中明确指定 `--framework fastapi` 以利用类型注解信息
- **当项目使用Express框架**：在步骤1中明确指定 `--framework express` 以识别JavaScript路由
- **当项目使用Django框架**：在步骤1中明确指定 `--framework django` 以识别DRF视图
- **当项目使用NestJS框架**：在步骤1中明确指定 `--framework nestjs` 以识别装饰器
- **当项目使用Spring Boot框架**：在步骤1中明确指定 `--framework spring` 以识别注解
- **当项目使用Gin框架**：在步骤1中明确指定 `--framework gin` 以识别Go路由
- **当项目使用Echo框架**：在步骤1中明确指定 `--framework echo` 以识别Go路由
- **当需要自定义模块分组**：在步骤2后，手动调整模块分组逻辑再生成文档

#### 前端框架分支

- **当项目使用React框架**：在步骤1中明确指定 `--framework react` 以识别组件
- **当项目使用Vue框架**：在步骤1中明确指定 `--framework vue` 以识别组件
- **当项目使用Angular框架**：在步骤1中明确指定 `--framework angular` 以识别组件
- **当项目使用Svelte框架**：在步骤1中明确指定 `--framework svelte` 以识别组件
- **当项目使用Next.js框架**：在步骤1中明确指定 `--framework nextjs` 以识别API路由
- **当项目使用Nuxt.js框架**：在步骤1中明确指定 `--framework nuxtjs` 以识别API路由

## 资源索引

### 必要脚本

- 见 [scripts/api_scanner.py](scripts/api_scanner.py)
  - 用途：扫描项目代码，提取API路由和参数信息
  - 参数：--project-dir, --framework, --output
- 见 [scripts/module_classifier.py](scripts/module_classifier.py)
  - 用途：基于路由路径自动划分模块和层级结构
  - 参数：--input, --output

### 领域参考

- 见 [references/doc-structure.md](references/doc-structure.md)
  - 何时读取：在步骤3生成文档结构时参考
  - 内容：API文档的标准章节结构和格式规范
- 见 [references/framework-patterns.md](references/framework-patterns.md)
  - 何时读取：理解脚本如何识别不同框架的路由定义
  - 内容：各Web框架的路由定义模式和识别规则
- 见 [references/frontend-frameworks.md](references/frontend-frameworks.md)
  - 何时读取：了解前端框架的API文档组织方式
  - 内容：前端框架的组件识别和文档生成最佳实践
- 见 [references/backend-frameworks.md](references/backend-frameworks.md)
  - 何时读取：了解后端框架的API文档组织方式
  - 内容：后端框架的路由识别和文档生成最佳实践
- 见 [references/api-doc-best-practices.md](references/api-doc-best-practices.md)
  - 何时读取：了解API文档的通用最佳实践
  - 内容：API文档的组织建议、格式规范和常见问题

### 输出资产

- 见 [assets/templates/](assets/templates/)
  - 用途：提供各章节和端点的文档模板
  - 包含：overview-template.md, endpoint-template.md, module-template.md

## 注意事项

- 脚本使用正则表达式和AST解析识别路由，对于复杂的动态路由可能无法完全识别，需要手动补充
- 参数提取依赖于代码注释和类型注解，建议在代码中完善文档字符串
- 模块划分基于路径的第一段，对于特殊结构可能需要手动调整
- 生成文档后，建议人工审核并补充业务说明、使用示例等
- 仅在需要时读取参考文档，保持上下文简洁
- 对于前端框架，组件识别依赖于组件定义模式，建议使用标准的组件定义方式
- 对于后端框架，路由识别依赖于框架特定的装饰器或方法调用，建议使用标准的路由定义方式

## 使用示例

### 示例1：Flask项目文档生成

```
# 1. 扫描Flask项目
python scripts/api_scanner.py \
  --project-dir /path/to/flask/project \
  --framework flask \
  --output api_scan_result.json

# 2. 划分模块
python scripts/module_classifier.py \
  --input api_scan_result.json \
  --output api_modules.json

# 3-4. 智能体根据模板生成完整文档
```

### 示例2：FastAPI项目文档生成

```
# FastAPI项目会自动识别类型注解和Pydantic模型
python scripts/api_scanner.py \
  --project-dir /path/to/fastapi/project \
  --framework fastapi

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例3：Express项目文档生成

```
# Node.js Express项目
python scripts/api_scanner.py \
  --project-dir /path/to/express/project \
  --framework express

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例4：React项目组件文档生成

```
# React项目组件文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/react/project \
  --framework react

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例5：Vue项目组件文档生成

```
# Vue项目组件文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/vue/project \
  --framework vue

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例6：Next.js项目API文档生成

```
# Next.js项目API路由文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/nextjs/project \
  --framework nextjs

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例7：Nuxt.js项目API文档生成

```
# Nuxt.js项目API路由文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/nuxtjs/project \
  --framework nuxtjs

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例8：Django项目文档生成

```
# Django REST Framework项目文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/django/project \
  --framework django

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例9：NestJS项目文档生成

```
# NestJS项目文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/nestjs/project \
  --framework nestjs

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例10：Spring Boot项目文档生成

```
# Spring Boot项目文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/spring/project \
  --framework spring

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例11：Gin项目文档生成

```
# Gin项目文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/gin/project \
  --framework gin

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例12：Echo项目文档生成

```
# Echo项目文档生成
python scripts/api_scanner.py \
  --project-dir /path/to/echo/project \
  --framework echo

python scripts/module_classifier.py \
  --input api_scan_result.json
```

### 示例13：自动检测框架

```
# 自动检测项目框架
python scripts/api_scanner.py \
  --project-dir /path/to/project \
  --framework auto

python scripts/module_classifier.py \
  --input api_scan_result.json
```

## 支持的框架

### 前端框架

- React
- Vue
- Angular
- Svelte
- Next.js
- Nuxt.js

### 后端框架

- Flask
- FastAPI
- Django
- Express
- NestJS
- Spring Boot
- Gin
- Echo

## 框架识别规则

### 后端框架检测优先级

1. 检测 `from fastapi import` 或 `FastAPI(` → FastAPI
2. 检测 `from flask import` 或 `Flask(` → Flask
3. 检测 `from django.urls import` 或 `from rest_framework import` → Django
4. 检测 `@Controller` 或 `@RestController` → Spring Boot
5. 检测 `@nestjs/common` → NestJS
6. 检测 `github.com/gin-gonic/gin` → Gin
7. 检测 `github.com/labstack/echo/v4` → Echo
8. 检测 `require('express')` 或 `express()` → Express

### 前端框架检测优先级

1. 检测 `import React` 或 `from 'react'` → React
2. 检测 `<template>` 标签或 `defineProps` → Vue
3. 检测 `@Component` 或 `@angular/core` → Angular
4. 检测 `<script>` 标签且没有 `lang="ts"` → Svelte
5. 检测 `next/server` 或 `pages/api/` → Next.js
6. 检测 `defineEventHandler` 或 `server/api/` → Nuxt.js

## 文档生成最佳实践

1. **代码注释**：在代码中添加清晰的docstring和注释
2. **类型注解**：使用类型注解（TypeScript、FastAPI、NestJS）
3. **标准命名**：使用标准的命名约定和代码结构
4. **人工审核**：生成文档后人工审核和补充
5. **定期更新**：定期更新文档以保持与代码同步

## 常见问题

### Q1: 如何提高路由识别准确率？

A: 在步骤1中明确指定框架类型，使用 `--framework` 参数。

### Q2: 如何自定义模块分组？

A: 在步骤2后，手动调整模块分组逻辑再生成文档。

### Q3: 如何处理复杂的动态路由？

A: 对于复杂的动态路由，可能无法完全识别，需要手动补充文档信息。

### Q4: 如何处理前端组件文档？

A: 使用 `--framework react/vue/angular/svelte` 参数，脚本会识别组件定义并生成组件文档。

### Q5: 如何处理Next.js/Nuxt.js的API路由？

A: 使用 `--framework nextjs/nuxtjs` 参数，脚本会识别API路由并生成API文档。

## 后续优化

1. 添加更多框架的支持
2. 优化识别算法，提高准确率
3. 添加文档质量检查功能
4. 支持多种文档输出格式（如 HTML、PDF）
5. 集成 CI/CD，自动生成和更新文档
