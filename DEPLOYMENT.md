# YoFinance 部署指南

## 🚀 快速部署

### 1. Vercel 部署（推荐）

#### 步骤 1: 准备项目
```bash
cd /Users/tomi/Documents/Program/YoFinance
git init
git add .
git commit -m "Initial commit: YoFinance"
```

#### 步骤 2: 推送到 GitHub
```bash
# 在 GitHub 上创建新仓库
# 然后推送代码
git remote add origin https://github.com/yourusername/x-finance.git
git push -u origin main
```

#### 步骤 3: 部署到 Vercel
1. 访问 [Vercel](https://vercel.com)
2. 连接 GitHub 账户
3. 导入项目
4. 配置环境变量
5. 部署

### 2. 环境变量配置

在 Vercel 项目设置中添加以下环境变量：

```bash
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
NEXT_PUBLIC_APP_URL=https://your-domain.vercel.app
NEXT_PUBLIC_APP_NAME=YoFinance
```

### 3. Supabase 设置

#### 步骤 1: 创建 Supabase 项目
1. 访问 [Supabase](https://supabase.com)
2. 创建新项目
3. 获取项目 URL 和 API Key

#### 步骤 2: 执行数据库脚本
在 Supabase SQL 编辑器中执行 `database/schema.sql` 文件

#### 步骤 3: 配置认证
1. 在 Supabase 控制台启用认证
2. 配置认证提供商（可选）
3. 设置重定向 URL

## 🔧 本地开发

### 1. 安装依赖
```bash
npm install
```

### 2. 配置环境变量
```bash
cp .env.example .env.local
# 编辑 .env.local 文件
```

### 3. 启动开发服务器
```bash
npm run dev
```

## 📊 数据库管理

### 1. 表结构
- `domains` - 域名主表
- `domain_transactions` - 交易记录表
- `domain_alerts` - 提醒设置表
- `domain_settings` - 用户设置表

### 2. 安全策略
所有表都启用了行级安全（RLS），确保数据隔离。

### 3. 索引优化
已为常用查询字段创建索引，提升查询性能。

## 🔒 安全配置

### 1. 环境变量安全
- 不要在代码中硬编码敏感信息
- 使用环境变量管理配置
- 定期轮换 API 密钥

### 2. 数据库安全
- 启用行级安全策略
- 限制数据库访问权限
- 定期备份数据

### 3. 应用安全
- 启用 HTTPS
- 实施 CSP 策略
- 输入验证和清理

## 📈 性能优化

### 1. 前端优化
- 使用 Next.js 自动优化
- 启用图片优化
- 实施代码分割

### 2. 数据库优化
- 创建适当的索引
- 使用连接池
- 监控查询性能

### 3. CDN 配置
- 使用 Vercel 的全球 CDN
- 启用静态资源缓存
- 配置适当的缓存策略

## 🚨 监控和日志

### 1. 错误监控
- 集成 Sentry 或类似服务
- 设置错误警报
- 监控应用性能

### 2. 用户分析
- 集成 Google Analytics
- 跟踪用户行为
- 分析使用模式

### 3. 数据库监控
- 使用 Supabase 内置监控
- 设置性能警报
- 监控查询性能

## 🔄 持续集成

### 1. GitHub Actions
```yaml
name: CI/CD
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run build
      - run: npm run lint
```

### 2. 自动部署
- 配置 Vercel 自动部署
- 设置预览环境
- 实施部署检查

## 📝 维护指南

### 1. 定期更新
- 更新依赖包
- 应用安全补丁
- 升级 Next.js 版本

### 2. 数据备份
- 定期备份数据库
- 导出用户数据
- 测试恢复流程

### 3. 性能监控
- 监控应用性能
- 分析用户反馈
- 优化慢查询

## 🆘 故障排除

### 1. 常见问题
- 环境变量配置错误
- 数据库连接问题
- 认证配置错误

### 2. 调试技巧
- 检查浏览器控制台
- 查看 Vercel 日志
- 使用 Supabase 调试工具

### 3. 联系支持
- GitHub Issues
- 社区论坛
- 技术支持邮箱

---

**注意**: 这是一个完整的部署指南，请根据实际需求调整配置。
