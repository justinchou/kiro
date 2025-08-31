# 创建指导文档

根据项目类型和需求，为开发项目创建全面的指导文档。

## 用法

```
为 [项目描述] 创建指导文档
```

## 示例

- `为 React TypeScript 电子商务应用程序创建指导文档`
- `为使用 PostgreSQL 的 Python Django REST API 创建指导文档`
- `为 Node.js 微服务架构创建指导文档`
- `为 Vue.js 组件库创建指导文档`

## 流程

您是创建项目指导文档的专家，这些文档为开发工作提供上下文指导。请遵循以下系统化方法：

### 1. 项目分析
首先，分析项目需求并确定需要哪些指导文档：

**对于前端项目 (React, Vue, Angular):**
- 包括: project-standards.md, git-workflow.md, frontend-standards.md, development-environment.md
- 考虑: component-library.md, testing-strategy.md

**对于后端/API 项目 (Node.js, Python, Java):**
- 包括: project-standards.md, git-workflow.md, api-design.md, development-environment.md
- 考虑: database-standards.md, security-guidelines.md

**对于全栈项目:**
- 包括: 所有核心文档以及特定于技术的文档
- 考虑: deployment-standards.md, monitoring-guidelines.md

**对于库/包项目:**
- 包括: project-standards.md, git-workflow.md, documentation-standards.md
- 考虑: versioning-strategy.md, publishing-guidelines.md

### 2. 文档创建策略

使用这些模板和指南创建指导文档：

#### 核心文档 (始终创建)

**project-standards.md** - #[[file:.kiro/steering/project-standards.md]]
- 根据项目语言/框架调整代码质量标准
- 根据项目复杂性自定义测试要求
- 包括项目特定的文档需求
- 设置与领域相关的安全实践

**git-workflow.md** - #[[file:.kiro/steering/git-workflow.md]]
- 根据团队规模和发布策略调整分支命名
- 根据项目需求自定义提交消息格式
- 设置适当的审查要求
- 定义合并策略

#### 条件文档 (根据项目类型创建)

**frontend-standards.md** - #[[file:.kiro/steering/frontend-standards.md]]
```yaml
---
inclusion: fileMatch
fileMatchPattern: '*.tsx|*.jsx|*.vue|*.svelte|*.ts|*.js'
---
```
- 针对特定框架 (React/Vue/Angular) 进行自定义
- 包括设计系统和样式方法
- 设置可访问性要求
- 定义性能标准

**api-design.md** - #[[file:.kiro/steering/api-design.md]]
```yaml
---
inclusion: fileMatch
fileMatchPattern: '*api*|*route*|*controller*|*endpoint*'
---
```
- 根据项目需求调整 REST/GraphQL 标准
- 包括身份验证/授权模式
- 设置错误处理约定
- 定义 API 版本控制策略

**development-environment.md** - #[[file:.kiro/steering/development-environment.md]]
```yaml
---
inclusion: fileMatch
fileMatchPattern: 'package.json|requirements.txt|Dockerfile|docker-compose.yml|Makefile'
---
```
- 针对项目的技术栈进行自定义
- 包括特定的工具要求
- 设置环境变量模式
- 定义构建和部署过程

### 3. 内容定制指南

**特定语言/框架的调整:**
- **JavaScript/TypeScript**: ESLint, Prettier, Jest, package.json 脚本
- **Python**: Black, flake8, pytest, requirements.txt, 虚拟环境
- **Java**: Checkstyle, Maven/Gradle, JUnit, Spring Boot 约定
- **Go**: gofmt, go mod, 测试模式, 项目结构
- **Rust**: rustfmt, Cargo.toml, cargo test, clippy

**项目规模调整:**
- **小型项目**: 轻量级流程, 最少的工具
- **团队项目**: 代码审查要求, 共享标准
- **企业级**: 全面的安全性、合规性和文档

**特定领域的考虑:**
- **电子商务**: PCI 合规性, 性能, 安全性
- **医疗保健**: HIPAA 合规性, 数据隐私, 审计跟踪
- **金融**: 安全标准, 法规遵从性
- **开源**: 贡献指南, 许可, 社区标准

### 4. 文件引用集成

使用 `#[[file:path]]` 语法包含相关的外部文件:
- API 项目的 OpenAPI 规范
- 后端项目的数据库模式
- 前端项目的设计系统令牌
- 环境设置的配置文件

### 5. 质量清单

在最终确定指导文档之前，请确保:
- [ ] 所有文档都具有用于包含逻辑的适当前置元数据
- [ ] 指南是具体且可操作的，而不是通用的
- [ ] 为复杂概念提供了示例
- [ ] 文档之间没有冲突的标准
- [ ] 包括了安全性和性能方面的考虑
- [ ] 文档涵盖了整个开发生命周期
- [ ] 文件引用格式正确且有效

## 参考资料

使用这些综合指南来创建指导文档：

**创建指南:** #[[file:.kiro/steering/steering-creation-guide.md]]

**模板示例:**
- #[[file:.kiro/steering/project-standards.md]]
- #[[file:.kiro/steering/git-workflow.md]]
- #[[file:.kiro/steering/frontend-standards.md]]
- #[[file:.kiro/steering/api-design.md]]
- #[[file:.kiro/steering/development-environment.md]]

## 输出格式

在 `.kiro/steering/` 目录中创建一套完整的指导文档，其中包含:
1. 用于包含逻辑的适当前置元数据
2. 特定于项目的内容和示例
3. 清晰、可操作的指南
4. 在适用的情况下正确的文件引用
5. 一致的格式和结构

指导文档应立即提高开发一致性，并为特定的项目需求提供上下文指导。