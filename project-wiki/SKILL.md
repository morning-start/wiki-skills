---
name: project-wiki
version: 7.1.0
description: 智能项目知识助手，支持模板 + 脚本快速生成标准文档、文档流程管理和知识库查询
tags: [project-wiki, documentation, knowledge-base, templates, generator]
---

# ProjectWiki - 智能项目知识助手

## 任务目标

ProjectWiki 是一个智能项目知识助手，帮助你快速生成标准项目文档、管理文档生命周期和查询技术知识。

**核心价值**:
- 🚀 **快速生成**: 5 分钟内生成 README、ARCHITECTURE 等标准文档
- 📋 **模板丰富**: 18+ 标准模板，覆盖基础文档、架构设计、需求文档等
- 🔧 **工具完善**: 交互式生成器 + 配置文件，提升文档效率
- 📚 **知识全面**: 技术框架、设计模式、最佳实践速查
- ✅ **质量保证**: 7 大类一致性检查，确保文档质量

---

## 快速上手（5 分钟）

### 1. 生成 README 文档

```bash
# 创建配置文件
cat > config.yaml << EOF
project_name: "My Project"
username: "octocat"
version: "1.0.0"
EOF

# 生成 README
uv run python scripts/generate_doc.py \
  --template basic/README.md \
  --output README.md \
  --config config.yaml
```

### 2. 查看可用模板

```bash
cd project-wiki
uv run python scripts/generate_doc.py --list
```

### 3. 生成架构文档

```bash
uv run python scripts/generate_doc.py \
  --template architecture/ARCHITECTURE.md \
  --output ARCHITECTURE.md \
  --config config.yaml
```

**完成!** 现在你有了 README.md 和 ARCHITECTURE.md 两个标准文档。

---

## 核心能力

### 1. 模板 + 脚本快速生成 ⭐⭐⭐⭐⭐

**触发场景**: 新项目启动、需要快速生成标准文档时

**输入**: 项目名称、作者等基本信息（可通过配置文件提供）

**输出**: 标准格式的 Markdown 文档

**示例**:
```bash
# 交互式生成
uv run python scripts/generate_doc.py \
  --template basic/README.md \
  --output ../my-project/README.md
```

### 2. 基础文档生成 ⭐⭐⭐⭐⭐

**触发场景**: 需要创建 README、CHANGELOG、CONTRIBUTING 等基础文档

**支持文档**:
- README.md - 项目说明
- CHANGELOG.md - 变更日志
- CONTRIBUTING.md - 贡献指南
- CODE_OF_CONDUCT.md - 行为准则
- LICENSE.md - 许可证

**示例**: 见"快速上手"章节

### 3. 架构设计文档生成 ⭐⭐⭐⭐

**触发场景**: 需要设计系统架构、API 接口、详细设计时

**支持模板**:
- ARCHITECTURE.md - 系统架构
- api-template.md - API 接口文档
- design-doc-template.md - 详细设计文档

**示例**:
```bash
uv run python scripts/generate_doc.py \
  --template architecture/api-template.md \
  --output wiki/api.md \
  --config config.yaml
```

### 4. 需求文档生成 ⭐⭐⭐⭐

**触发场景**: 需要收集需求、编写功能说明、需求追踪时

**支持模板**:
- functional-doc-template.md - 功能需求文档
- requirement-doc-template.md - 详细需求文档
- rtm-template.md - 需求追踪矩阵

### 5. 文档一致性检查 ⭐⭐⭐⭐

**触发场景**: 版本发布前、需求变更后、定期质量检查

**检查项**: 术语命名、内容逻辑、格式结构、数据参数、图表文字、角色权限、时间进度

**示例**:
```bash
# 使用一致性检查清单
uv run python scripts/check_consistency.py \
  --docs README.md,ARCHITECTURE.md,CHANGELOG.md
```

### 6. 项目类型指南 ⭐⭐⭐

**触发场景**: 针对特定类型项目（前端/后端/全栈等）编写文档

**支持类型**: 前端、后端、全栈、移动端、桌面端、CLI/TUI、游戏项目

### 7. 知识库查询 ⭐⭐⭐

**触发场景**: 技术选型、架构设计、需要最佳实践参考时

**知识库内容**:
- 技术框架速查
- 设计模式速查
- 设计原则速查
- 一致性规则
- 工具链指南

---

## 使用示例

### 场景 1: 快速生成项目文档（推荐）

适用于新项目快速启动。

```bash
# 1. 准备配置文件
cat > doc-config.yaml << EOF
project_name: "Awesome Project"
username: "your-username"
version: "1.0.0"
description: "项目描述"
contact_email: "contact@example.com"
EOF

# 2. 批量生成文档
uv run python scripts/generate_doc.py -t basic/README.md -o README.md -c doc-config.yaml
uv run python scripts/generate_doc.py -t basic/CHANGELOG.md -o CHANGELOG.md -c doc-config.yaml
uv run python scripts/generate_doc.py -t architecture/ARCHITECTURE.md -o ARCHITECTURE.md -c doc-config.yaml
```

**检验结果**: ✅ 3 个标准文档已生成

### 场景 2: 生成 API 文档

适用于前后端项目需要 API 接口文档。

```bash
# 生成 API 文档
uv run python scripts/generate_doc.py \
  --template architecture/api-template.md \
  --output wiki/api.md \
  --config doc-config.yaml
```

**填写变量**:
```
api_name (必填): User API
endpoint (必填): /api/users
method (必填): POST
```

**检验结果**: ✅ API 文档已生成

### 场景 3: 版本发布前一致性检查

适用于版本发布前确保文档一致性。

**步骤**:

1. 检查版本号一致性
```bash
# 检查 SKILL.md、CHANGELOG.md、Git Tag 版本号
grep "version:" SKILL.md
grep "## \[" CHANGELOG.md
git tag -l
```

2. 使用检查清单逐项检查
```
□ 术语与命名一致性
□ 内容逻辑正确
□ 格式与结构规范
□ 数据与参数准确
□ 图表与文字一致
□ 角色与权限清晰
□ 时间与进度合理
```

**检验结果**: ✅ 所有检查项通过

### 场景 4: 需求变更后同步更新

适用于需求变更后同步更新相关文档。

**步骤**:

1. 更新需求文档
```bash
# 修改 requirement-docs/REQ-003.md
# 更新功能描述和验收标准
```

2. 同步更新设计文档
```bash
# 修改 design-docs/design-003.md
# 更新 3.2.3 章节和接口定义
```

3. 验证一致性
```bash
# 使用 RTM 验证需求 - 设计 - 测试对齐
uv run python scripts/verify_rtm.py
```

**检验结果**: ✅ 文档一致性已验证

### 场景 5: 查询技术框架信息

适用于技术选型时快速了解框架信息。

```bash
# 查阅知识库
cat references/knowledge/frameworks.md

# 查找特定框架
grep -A 10 "React" references/knowledge/frameworks.md
```

**获取信息**:
- 框架特点
- 适用场景
- 最佳实践
- 配置示例

**检验结果**: ✅ 获取所需信息

---

## 工作流程

### 简化版流程

```
1. 选择模板 → 2. 填写变量 → 3. 生成文档
```

### 详细版流程

#### 第一步：查阅信息

1. 分析项目类型（前端/后端/全栈等）
2. 确定需要的文档类型
3. 查阅知识库获取最佳实践

#### 第二步：执行操作

1. 选择对应模板
2. 使用生成器或手动填写
3. 生成文档初稿

#### 第三步：检查验收

1. 验证文档完整性
2. 运行一致性检查
3. 确认格式规范
4. 生成检查报告

---

## 参考文档

### 高频使用

| 文档 | 用途 | 路径 |
|------|------|------|
| 快速开始 | 5 分钟上手 | [QUICKSTART.md](QUICKSTART.md) |
| 使用指南 | 详细说明 | [scripts/README.md](scripts/README.md) |
| 模板索引 | 查看所有模板 | [templates/](templates/) |

### 中频使用

| 文档 | 用途 | 路径 |
|------|------|------|
| 文档指南索引 | 编写指南 | [references/guides/](references/guides/) |
| 架构文档指南 | 编写 ARCHITECTURE | [guides/architecture-doc-guide.md](references/guides/architecture-doc-guide.md) |
| API 文档指南 | 编写 API 文档 | [guides/api-doc-guide.md](references/guides/api-doc-guide.md) |

### 低频使用

| 文档 | 用途 | 路径 |
|------|------|------|
| 项目类型指南 | 特定类型项目 | [references/guides/](references/guides/) |
| 文档管理指南 | 建立管理流程 | [guides/document-management-guide.md](references/guides/document-management-guide.md) |
| 知识库 | 技术参考 | [references/knowledge/](references/knowledge/) |

---

## 常见问题（FAQ）

### Q1: 找不到模板怎么办？

**A**: 使用 `--list` 命令查看所有可用模板：

```bash
uv run python scripts/generate_doc.py --list
```

确保模板路径正确，例如 `basic/README.md`。

### Q2: 配置文件不生效怎么办？

**A**: 检查以下几点：

1. 配置文件格式是否正确（YAML/JSON）
2. 变量名是否与模板中的一致
3. 使用 `--config` 参数指定正确路径

```bash
# 检查配置文件
cat config.yaml

# 使用配置
uv run python scripts/generate_doc.py --config config.yaml ...
```

### Q3: 变量未替换怎么办？

**A**: 确保变量格式正确：

- 正确：`{{variable_name}}`
- 错误：`{variable_name}` 或 `{{variableName}}`

检查模板中的变量名，确保完全匹配。

### Q4: 如何自定义模板？

**A**: 有两种方式：

1. **复制模板修改**:
```bash
cp templates/basic/README.md my-custom-template.md
# 编辑 my-custom-template.md
```

2. **创建自定义目录**:
```bash
mkdir -p templates/custom
# 将自定义模板放在 templates/custom/ 目录
```

### Q5: 如何批量生成文档？

**A**: 创建批量生成脚本：

```bash
#!/bin/bash
# generate-all.sh

CONFIG="config.yaml"
GENERATOR="scripts/generate_doc.py"

uv run python $GENERATOR -t basic/README.md -o README.md -c $CONFIG
uv run python $GENERATOR -t basic/CHANGELOG.md -o CHANGELOG.md -c $CONFIG
uv run python $GENERATOR -t architecture/ARCHITECTURE.md -o ARCHITECTURE.md -c $CONFIG

echo "✅ 所有文档已生成"
```

执行：
```bash
chmod +x generate-all.sh
./generate-all.sh
```

### Q6: 如何更新已生成的文档？

**A**: 直接编辑生成的文件，或重新运行生成器（会提示是否覆盖）：

```bash
# 重新生成（提示覆盖）
uv run python scripts/generate_doc.py \
  --template basic/README.md \
  --output README.md \
  --config config.yaml
```

### Q7: 支持哪些配置文件格式？

**A**: 支持 YAML 和 JSON 格式：

- YAML: `config.yaml`（推荐）
- JSON: `config.json`

示例见 [config.example.yaml](scripts/config.example.yaml)。

---

## 注意事项

- **使用生成器**: 优先使用 `generate_doc.py` 快速生成标准文档
- **标准化优先**: 使用统一的变量格式 `{{variable_name}}`
- **渐进式完善**: 从核心文档开始，逐步完善
- **保持一致性**: 确保术语、版本、配置在各文档间一致
- **及时更新**: 代码变更时同步更新文档
- **定期验证**: 版本发布前必须进行一致性检查
- **使用工具**: 充分利用自动化检查工具
- **文档评审**: 重要文档变更需经过同行评审

---

## 命令速查

```bash
# 列出模板
uv run python scripts/generate_doc.py --list

# 生成单个文档
uv run python scripts/generate_doc.py -t basic/README.md -o README.md

# 使用配置文件
uv run python scripts/generate_doc.py -t basic/README.md -o README.md -c config.yaml

# 标准化模板变量
uv run python scripts/normalize_templates.py --templates-dir templates

# 查看变量报告
cat variable_report.md
```

## 模板速查

| 分类 | 模板 | 用途 |
|------|------|------|
| **基础** | basic/README.md | 项目说明 |
| **基础** | basic/CHANGELOG.md | 变更日志 |
| **架构** | architecture/ARCHITECTURE.md | 系统架构 |
| **架构** | architecture/api-template.md | API 文档 |
| **需求** | requirements/functional-doc-template.md | 功能需求 |
| **规划** | roadmap/ROADMAP.md | 项目路线图 |

## 变量格式

- `{{variable_name}}` - 普通变量
- `{{*variable_name}}` - 必填变量
- `{{?variable_name}}` - 可选变量

---

**最后更新**: 2026-03-06  
**版本**: v7.1.0  
**状态**: ✅ 可用
