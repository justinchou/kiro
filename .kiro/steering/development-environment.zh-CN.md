---
inclusion: fileMatch
fileMatchPattern: 'package.json|requirements.txt|Dockerfile|docker-compose.yml'
---

# 开发环境设置

## 本地开发
- 使用 .nvmrc 文件中指定的 Node.js 版本
- 使用 `npm ci` 安装依赖以确保构建一致
- 使用 Docker 管理本地数据库和服务依赖
- 在提交更改前运行代码检查和格式化

## 环境变量
- 将 `.env.example` 复制为 `.env` 用于本地开发
- 切勿提交实际的环境文件
- 在 README 中记录所有必需的环境变量
- 为不同环境使用不同的前缀 (DEV_, PROD_ 等)

## 数据库管理
- 对所有模式更改使用迁移
- 为迁移包含回滚脚本
- 种子数据应是幂等的
- 在重大更改前备份数据库

## 构建和部署
- 确保构建在不同环境中是可复现的
- 使用多阶段 Docker 构建进行优化
- 在容器化应用中包含健康检查
- 记录部署过程和回滚步骤

## 调试和日志记录
- 使用结构化日志记录及适当的日志级别
- 包含用于请求跟踪的相关 ID
- 设置正确的错误监控和警报
- 在开发中使用调试器而非 console.log