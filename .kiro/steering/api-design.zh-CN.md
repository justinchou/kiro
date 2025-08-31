---
inclusion: manual
---

# API 设计准则

## RESTful API 标准
- 恰当使用 HTTP 方法 (GET, POST, PUT, DELETE, PATCH)
- 遵循基于资源的 URL 模式：`/api/v1/users/{id}`
- 对资源集合使用复数名词
- 实现正确的 HTTP 状态码
- 在 URL 路径中包含 API 版本

## 请求/响应格式
- 对请求和响应体使用 JSON
- 遵循一致的命名约定 (camelCase 或 snake_case)
- 为列表端点包含分页
- 实现正确的错误响应格式：
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
- 实现正确的令牌刷新机制
- 使用基于角色的访问控制 (RBAC)
- 对 API 端点进行速率限制以防止滥用

## 文档
- 使用 OpenAPI/Swagger 进行 API 文档记录
- 包含请求/响应示例
- 记录所有可能的错误响应
- 提供 SDK 或客户端库示例

#[[file:openapi.yml]]