# 创建指导文档 - 独立版

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

**project-standards.md 模板:**
```markdown
# 项目标准和指南

## 代码质量标准
- 遵循特定语言的风格指南 (JS/TS 使用 ESLint, Python 使用 Black 等)
- 在整个代码库中保持一致的命名约定
- 编写带有清晰变量和函数名称的自文档化代码
- 为复杂的业务逻辑添加有意义的注释
- 保持函数短小并专注于单一职责

## 测试要求
- 为所有业务逻辑函数编写单元测试
- 保持最低 80% 的代码覆盖率
- 为 API 端点添加集成测试
- 为关键用户流程编写端到端测试
- 使用描述性测试名称来解释正在测试的场景

## 文档标准
- 对任何重大更改更新 README.md
- 使用清晰的示例记录 API 端点
- 包括设置和部署说明
- 维护版本发布的变更日志
- 以 ADR 格式记录架构决策

## 安全实践
- 切勿提交机密、API 密钥或密码
- 使用环境变量进行配置
- 验证所有用户输入
- 实施适当的身份验证和授权
- 遵循 OWASP 安全指南

## 性能指南
- 优化数据库查询并避免 N+1 问题
- 在适当的地方实施缓存
- 对大型数据集使用延迟加载
- 定期监控和分析性能
- 在架构决策中考虑可伸缩性
```

**git-workflow.md 模板:**
```markdown
# Git 工作流和分支策略

## 分支命名约定
- 功能分支: `feature/description-of-feature`
- 错误修复: `fix/description-of-bug`
- 紧急修复: `hotfix/critical-issue-description`
- 发布: `release/version-number`

## 提交消息格式
遵循 conventional commits 格式:
```
type(scope): description

[可选的正文]

[可选的页脚]
```

类型: feat, fix, docs, style, refactor, test, chore

## 拉取请求指南
- 从功能分支创建到 main/develop 的 PR
- 包括清晰的更改描述
- 使用关键字链接相关问题 (fixes #123)
- 在请求审查之前确保所有测试通过
- 合并时压缩提交以保持历史记录清晰

## 代码审查流程
- 合并前至少需要一次批准
- 审查代码质量、安全性和性能
- 检查测试是否覆盖新功能
- 验证文档是否根据需要更新
- 确保在没有适当版本控制的情况下没有重大更改
```

#### 条件文档 (根据项目类型创建)

**frontend-standards.md 模板:**
```markdown
---
inclusion: fileMatch
fileMatchPattern: '*.tsx|*.jsx|*.vue|*.svelte'
---

# 前端开发标准

## 组件架构
- 使用带有钩子的函数式组件 (React)
- 保持组件短小且专注
- 实施适当的 prop 验证
- 使用 TypeScript 以确保类型安全
- 遵循组件组合模式

## 状态管理
- 对组件特定数据使用本地状态
- 为共享应用程序数据实施全局状态
- 使用适当的状态管理库 (Redux, Zustand, Pinia)
- 避免使用上下文或状态管理进行 prop drilling

## 样式指南
- 使用 CSS 模块或 styled-components 进行组件样式设置
- 遵循 BEM 方法进行 CSS 类命名
- 采用移动优先的方法实施响应式设计
- 使用 CSS 自定义属性进行主题化
- 保持一致的间距和排版比例

## 性能优化
- 实施代码拆分和延迟加载
- 对昂贵的组件使用 React.memo 或类似方法
- 优化图像和资产
- 实施适当的缓存策略
- 监控捆绑包大小和性能指标

## 可访问性标准
- 使用语义化 HTML 元素
- 实施适当的 ARIA 属性
- 确保键盘导航支持
- 保持适当的颜色对比度
- 使用屏幕阅读器进行测试

## 测试策略
- 为实用程序函数编写单元测试
- 使用 React Testing Library 进行组件测试
- 实施视觉回归测试
- 测试用户交互和工作流程
- 正确模拟外部依赖项
```

**api-design.md 模板:**
```markdown
---
inclusion: manual
---

# API 设计指南

## RESTful API 标准
- 恰当使用 HTTP 方法 (GET, POST, PUT, DELETE, PATCH)
- 遵循基于资源的 URL 模式: `/api/v1/users/{id}`
- 对资源集合使用复数名词
- 实施适当的 HTTP 状态码
- 在 URL 路径中包含 API 版本控制

## 请求/响应格式
- 对请求和响应正文使用 JSON
- 遵循一致的命名约定 (camelCase 或 snake_case)
- 为列表端点添加分页
- 实施适当的错误响应格式:
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "提供的输入无效",
    "details": ["需要电子邮件", "密码太短"]
  }
}
```

## 身份验证和授权
- 使用 JWT 令牌进行无状态身份验证
- 实施适当的令牌刷新机制
- 使用基于角色的访问控制 (RBAC)
- 对 API 端点进行速率限制以防止滥用

## 文档
- 使用 OpenAPI/Swagger 进行 API 文档记录
- 包括请求/响应示例
- 记录所有可能的错误响应
- 提供 SDK 或客户端库示例

#[[file:openapi.yml]]
```

**development-environment.md 模板:**
```markdown
---
inclusion: fileMatch
fileMatchPattern: 'package.json|requirements.txt|Dockerfile|docker-compose.yml'
---

# 开发环境设置

## 本地开发
- 使用 .nvmrc 文件中指定的 Node.js 版本
- 使用 `npm ci` 安装依赖项以实现一致的构建
- 使用 Docker 处理本地数据库和服务依赖项
- 在提交更改之前运行 linting 和格式化

## 环境变量
- 将 `.env.example` 复制到 `.env` 以进行本地开发
- 切勿提交实际的环境文件
- 在 README 中记录所有必需的环境变量
- 为不同环境使用不同的前缀 (DEV_, PROD_ 等)

## 数据库管理
- 对所有模式更改使用迁移
- 为迁移添加回滚脚本
- 种子数据应是幂等的
- 在重大更改之前备份数据库

## 构建和部署
- 确保构建在不同环境中是可重现的
- 使用多阶段 Docker 构建进行优化
- 在容器化应用程序中添加健康检查
- 记录部署过程和回滚步骤

## 调试和日志记录
- 使用具有适当日志级别的结构化日志记录
- 为请求跟踪添加关联 ID
- 设置适当的错误监控和警报
- 在开发中使用调试器而不是 console.log
```

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

## 指导文档创建和使用指南

### 什么是指导文档?

指导文档是影响 AI 助手如何处理开发任务的上下文指南。它们包含项目特定的标准、约定和最佳实践，有助于提供更相关和一致的帮助。

### 指导文档如何工作

#### 包含机制
1. **始终包含 (默认)**: 没有前置元数据的文档包含在每次交互中
2. **文件匹配条件**: 具有 `inclusion: fileMatch` 和 `fileMatchPattern` 的文档在特定文件在上下文中时包含
3. **手动包含**: 具有 `inclusion: manual` 的文档仅在用 `#steering-name` 显式引用时包含

#### 上下文集成
- 在处理用户请求之前，指导内容被注入到 AI 的系统上下文中
- AI 接收适用的指导文档的全部内容
- 可以同时激活多个指导文档
- 使用 `#[[file:path]]` 语法的文件引用被解析并包含

### 指导文档中应包含什么

#### 要创建的核心类别:

1. **开发环境标准**
   - 本地设置过程
   - 工具配置
   - 环境变量管理
   - 构建和部署过程

2. **代码质量指南**
   - 特定语言的风格指南
   - 命名约定
   - 代码组织模式
   - 文档要求

3. **Git 工作流标准**
   - 分支命名约定
   - 提交消息格式
   - 拉取请求过程
   - 代码审查指南

4. **特定于技术的标准**
   - 前端开发模式
   - 后端 API 设计
   - 数据库管理
   - 测试策略

5. **安全性和性能**
   - 安全最佳实践
   - 性能优化指南
   - 监控和警报标准

#### 要遵循的内容结构:

```markdown
---
inclusion: [always|fileMatch|manual]
fileMatchPattern: 'pattern' # 仅当 fileMatch 时
---

# 清晰的标题

## 有组织的章节
- 具体、可操作的指南
- 相关的代码示例
- 工具配置
- 使用 #[[file:path]] 引用外部文件

## 实施细节
- 分步过程
- 要避免的常见陷阱
- 质量检查点
```

### 如何构建指导文档

#### 评估过程:
1. **项目分析**: 检查代码库结构、使用的技术和现有模式
2. **差距识别**: 确定标准可以提高一致性的领域
3. **优先级排序**: 首先关注高影响领域 (安全性、代码质量、工作流)
4. **模板选择**: 根据项目类型选择合适的模板

#### 内容开发:
1. **研究最佳实践**:借鉴行业标准和经过验证的模式
2. **针对项目进行情境化**: 将通用实践调整为特定的项目需求
3. **包括示例**: 提供具体的代码示例和配置
4. **引用集成**: 链接到现有的项目文件和规范

#### 质量保证:
1. **完整性检查**: 确保涵盖所有关键领域
2. **一致性验证**: 验证指南之间没有冲突
3. **实用性评估**: 确认指南是可操作和现实的
4. **更新机制**: 计划随着项目的发展维护文档

### 包含策略和上下文传输

#### 发送什么:
- **全部内容**: 传输完整的指导文档内容
- **解析的引用**: 读取并包含用 `#[[file:path]]` 引用的文件
- **多个文档**: 合并所有适用的指导文档
- **实时评估**: 为每次交互评估包含规则

#### 何时包含文档:
- **始终**: 没有前置元数据的文档的默认行为
- **文件上下文触发器**: 当特定文件模式在对话上下文中时
- **手动触发器**: 当用户使用 `#steering-name` 显式引用时
- **自动解析**: 系统根据文件模式确定相关性

#### 上下文限制:
- 如果超出上下文限制，大型指导文档可能会被截断
- 优先考虑更具体/相关的指导文档
- 最近的交互可能会影响优先考虑哪些文档

### 创建指导的最佳实践

#### 要做:
- 保持文档专注和具体
- 使用清晰、可操作的语言
- 包括具体示例
- 引用外部规范
- 随着项目的发展定期更新
- 使用适当的包含机制

#### 不要:
- 创建过于宽泛或通用的指南
- 在多个文档中重复信息
- 包括敏感信息或机密
- 创建冲突的标准
- 使文档过长或复杂

### 维护和演进

#### 定期审查:
- 评估现有指导文档的有效性
- 根据项目变更和学习进行更新
- 删除过时或冲突的指南
- 随着项目的发展添加新标准

#### 反馈集成:
- 监控指导文档对代码质量的影响程度
- 根据团队反馈和开发模式进行调整
- 优化包含模式以提高相关性
- 优化文档结构以提高清晰度

### 技术实施说明

#### 文件结构:
```
.kiro/steering/
├── project-standards.md (始终包含)
├── git-workflow.md (始终包含)
├── frontend-standards.md (fileMatch: *.tsx,*.jsx)
├── api-design.md (手动包含)
└── development-environment.md (fileMatch: package.json)
```

#### 前置元数据选项:
```yaml
---
inclusion: always|fileMatch|manual
fileMatchPattern: 'glob-pattern' # 仅用于 fileMatch
---
```

#### 文件引用语法:
```markdown
#[[file:relative/path/to/file.ext]]
```

## 输出格式

在 `.kiro/steering/` 目录中创建一套完整的指导文档，其中包含:
1. 用于包含逻辑的适当前置元数据
2. 特定于项目的内容和示例
3. 清晰、可操作的指南
4. 在适用的情况下正确的文件引用
5. 一致的格式和结构

指导文档应立即提高开发一致性，并为特定的项目需求提供上下文指导。