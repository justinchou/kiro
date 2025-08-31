# Git 工作流和分支策略

## 分支命名约定
- 功能分支：`feature/description-of-feature`
- 错误修复：`fix/description-of-bug`
- 紧急修复：`hotfix/critical-issue-description`
- 发布：`release/version-number`

## 提交信息格式
遵循常规提交格式：
```
type(scope): description

[optional body]

[optional footer]
```

类型：feat, fix, docs, style, refactor, test, chore

## 拉取请求指南
- 从功能分支创建到 main/develop 的 PR
- 包含清晰的更改描述
- 使用关键字链接相关问题 (fixes #123)
- 在请求审查前确保所有测试通过
- 合并时压缩提交以保持历史记录清晰

## 代码审查流程
- 合并前至少需要一次批准
- 审查代码质量、安全性和性能
- 检查测试是否覆盖新功能
- 如果需要，验证文档是否已更新
- 确保在没有正确版本控制的情况下没有重大更改