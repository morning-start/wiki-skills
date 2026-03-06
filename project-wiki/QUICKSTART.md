# 快速开始 - 5 分钟生成项目文档

本指南演示如何在 5 分钟内使用模板生成器为新项目生成完整的文档。

## 命令速查

```bash
# 列出所有模板
uv run python scripts/generate_doc.py --list

# 生成单个文档
uv run python scripts/generate_doc.py -t basic/README.md -o README.md

# 使用配置文件
uv run python scripts/generate_doc.py -t basic/README.md -o README.md -c config.yaml

# 覆盖已存在文件
uv run python scripts/generate_doc.py -t basic/README.md -o README.md -c config.yaml --overwrite

# 标准化模板变量
uv run python scripts/normalize_templates.py --templates-dir templates
```

## 变量格式速查

| 格式 | 说明 | 示例 |
|------|------|------|
| `{{variable_name}}` | 普通变量 | `{{project_name}}` |
| `{{*variable_name}}` | 必填变量 | `{{*username}}` |
| `{{?variable_name}}` | 可选变量 | `{{?description}}` |

## 模板分类速查

| 分类 | 常用模板 | 用途 |
|------|----------|------|
| **基础** | basic/README.md | 项目说明文档 |
| **基础** | basic/CHANGELOG.md | 变更日志 |
| **架构** | architecture/ARCHITECTURE.md | 系统架构设计 |
| **架构** | architecture/api-template.md | API 接口文档 |
| **需求** | requirements/functional-doc-template.md | 功能需求文档 |
| **规划** | roadmap/ROADMAP.md | 项目路线图 |

## 配置文件示例

```yaml
# config.yaml
project_name: "My Project"
username: "your-username"
version: "1.0.0"
description: "项目描述"
contact_email: "contact@example.com"
author: "作者姓名"
```

## 故障排查速查

| 问题 | 检查项 | 解决方案 |
|------|--------|----------|
| 找不到模板 | 模板路径 | 使用 `--list` 查看所有模板 |
| 配置文件不生效 | 文件格式 | 检查 YAML/JSON 格式 |
| 变量未替换 | 变量名匹配 | 确保变量名完全一致 |
| 命令执行失败 | Python 环境 | 使用 `uv run python` |

---

## 场景：为新项目生成文档

假设你刚创建了一个新项目 `my-awesome-project`，现在需要生成标准的 README、ARCHITECTURE 等文档。

## 步骤 1：准备配置文件（1 分钟）

```bash
# 进入项目目录
cd my-awesome-project

# 创建配置文件
cat > doc-config.yaml << EOF
# 项目基本信息
project_name: "My Awesome Project"
username: "your-github-username"
description: "一个超棒的项目，用于演示文档生成"
version: "1.0.0"

# 联系信息
contact_email: "contact@example.com"
author: "Your Name"

# 许可证
license_type: "MIT"
year: "2024"
EOF
```

## 步骤 2：生成 README 文档（1 分钟）

```bash
# 使用生成器创建 README
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/README.md \
  --output README.md \
  --config doc-config.yaml
```

脚本会提示你填写剩余变量（如果有）。大部分变量已从配置文件自动填充。

## 步骤 3：生成架构文档（2 分钟）

```bash
# 生成架构文档
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template architecture/ARCHITECTURE.md \
  --output ARCHITECTURE.md \
  --config doc-config.yaml
```

在交互模式下，填写技术栈和架构图等信息：

```
tech_stack (必填): React, TypeScript, Node.js, PostgreSQL
architecture_diagram (可选): [留空，稍后手动补充]
```

## 步骤 4：生成贡献指南（1 分钟）

```bash
# 生成贡献指南
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/CONTRIBUTING.md \
  --output CONTRIBUTING.md \
  --config doc-config.yaml
```

## 完成！

现在你有了：
- ✅ README.md - 项目说明
- ✅ ARCHITECTURE.md - 架构设计
- ✅ CONTRIBUTING.md - 贡献指南

可以继续生成其他文档：

```bash
# 许可证
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/LICENSE.md \
  --output LICENSE.md \
  --config doc-config.yaml

# 变更日志
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/CHANGELOG.md \
  --output CHANGELOG.md \
  --config doc-config.yaml

# 路线图
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template roadmap/ROADMAP.md \
  --output ROADMAP.md \
  --config doc-config.yaml
```

## 查看生成的文档

```bash
# 查看 README
cat README.md

# 查看架构
cat ARCHITECTURE.md

# 或者用编辑器打开
code README.md
code ARCHITECTURE.md
```

## 后续优化

生成的文档已经符合标准格式，你可以：

1. **补充架构图**：在 ARCHITECTURE.md 中添加 Mermaid 图表
2. **完善功能列表**：在 README.md 中列出具体功能
3. **添加 API 文档**：使用 `architecture/api-template.md` 生成 API 文档
4. **规划里程碑**：编辑 ROADMAP.md 添加具体时间点

## 高级技巧

### 技巧 1：复用配置

将配置文件放在工作区根目录，所有项目共享：

```bash
# 工作区配置
~/workspace/doc-config.yaml

# 在各项目中引用
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/README.md \
  --output README.md \
  --config ~/workspace/doc-config.yaml
```

### 技巧 2：批量生成脚本

创建 `generate-docs.sh`：

```bash
#!/bin/bash

CONFIG="doc-config.yaml"
GENERATOR="../wiki-skills/project-wiki/scripts/generate_doc.py"

echo "📦 生成项目文档..."

uv run python $GENERATOR \
  --template basic/README.md \
  --output README.md \
  --config $CONFIG

uv run python $GENERATOR \
  --template architecture/ARCHITECTURE.md \
  --output ARCHITECTURE.md \
  --config $CONFIG

uv run python $GENERATOR \
  --template basic/CONTRIBUTING.md \
  --output CONTRIBUTING.md \
  --config $CONFIG

echo "✅ 文档生成完成！"
```

使用：

```bash
chmod +x generate-docs.sh
./generate-docs.sh
```

### 技巧 3：查看可用模板

```bash
# 列出所有模板
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py --list

# 查看模板详情
cat ../wiki-skills/project-wiki/templates/basic/README.md
```

### 技巧 4：不使用配置文件

直接交互式填写：

```bash
uv run python ../wiki-skills/project-wiki/scripts/generate_doc.py \
  --template basic/README.md \
  --output README.md
```

脚本会逐个提示你填写变量。

## 常见问题

### Q: 找不到模板？

**A**: 确保路径正确，使用 `--list` 查看所有可用模板。

### Q: 配置文件不生效？

**A**: 检查 YAML 格式，确保变量名与模板中的一致。

### Q: 想修改生成的文档？

**A**: 直接编辑生成的文件即可，配置文件可以重复使用。

## 参考文档

- [完整使用指南](../project-wiki/scripts/README.md)
- [模板生成器总览](../project-wiki/TEMPLATE_GENERATOR.md)
- [配置文件示例](../project-wiki/scripts/config.example.yaml)

---

**提示**: 首次使用建议先阅读 [TEMPLATE_GENERATOR.md](../project-wiki/TEMPLATE_GENERATOR.md) 了解完整功能。
