---
title: Authentication
excerpt: Set up the authentication for your API to help users manage their credentials.
api_config: authentication
hidden: true
icon: icon-key1
link:
  new_tab: false
---
# 身份验证

本文档将指导您如何设置和管理API凭据，确保您的应用程序能够安全地访问我们的服务。

<Cards columns="2">
  <Card title="Email API 认证" href="#email-api-authentication" icon="envelope">
    了解如何为Email API端点配置认证参数
  </Card>
  <Card title="SMS API 认证" href="#sms-api-authentication" icon="sms">
    了解如何为SMS API端点配置认证参数
  </Card>
</Cards>

## Email API Authentication

Email API使用基于参数的身份验证方式，所有请求都需要在请求参数中包含您的凭据。

### 认证参数

<Tabs>
  <Tab title="必需参数">
每个Email API请求都必须包含以下两个参数：

| 参数名 | 描述 | 示例 |
|--------|------|------|
| `api_user` | 您的API用户名 | `mycompany_api` |
| `api_key` | 您的API密码/密钥 | `abc123def456...` |

> ⚠️ **重要提示**: 这些参数应直接包含在请求参数中，而不是通过HTTPS基本认证或请求头传递。
  </Tab>
  <Tab title="请求示例">
```bash
# GET 请求示例
curl "https://api.example.com/email/send?api_user=mycompany_api&api_key=abc123def456&to=user@example.com&subject=Hello"

# POST 请求示例
curl -X POST "https://api.example.com/email/send" \
  -d "api_user=mycompany_api" \
  -d "api_key=abc123def456" \
  -d "to=user@example.com" \
  -d "subject=Hello World"
```
  </Tab>
</Tabs>

### 凭据管理

<Accordion title="获取和创建凭据" icon="key">
**在哪里找到您的凭据：**

1. 登录您的账户
2. 从主菜单导航到 **Email API** 页面
3. 选择 **API Key Management** 部分

**可用操作：**
- ✅ 创建新的 `API_USER`（遵循平台命名规范）
- 🔑 为用户生成关联的 `API_KEY`
- 🔄 重置现有的 `API_KEY`
</Accordion>

<Accordion title="安全重置流程" icon="shield-alt">
**重置API密钥时的安全机制：**

- ⏰ **15分钟宽限期**：重置后，旧密钥在15分钟内仍然有效
- 🔄 **平滑过渡**：为您提供充足时间更新集成配置
- ⚡ **自动失效**：宽限期结束后旧密钥自动失效

**最佳实践：**
```bash
# 1. 重置密钥
# 2. 立即测试新密钥
curl "https://api.example.com/test?api_user=youruser&api_key=NEW_KEY"
# 3. 更新生产环境配置
# 4. 确保在15分钟内完成切换
```
</Accordion>

## SMS API Authentication

SMS API同样使用基于参数的身份验证，但使用不同的参数名称和管理流程。

### 认证参数

<Tabs>
  <Tab title="必需参数">
每个SMS API请求都必须包含以下两个参数：

| 参数名 | 描述 | 示例 |
|--------|------|------|
| `sms_user` | 您的SMS用户名 | `mycompany_sms` |
| `sms_key` | 您的SMS密码/密钥 | `xyz789uvw123...` |

> ⚠️ **重要提示**: 与Email API类似，这些参数需要直接包含在请求参数中。
  </Tab>
  <Tab title="请求示例">
```bash
# GET 请求示例
curl "https://api.example.com/sms/send?sms_user=mycompany_sms&sms_key=xyz789uvw123&to=+1234567890&message=Hello"

# POST 请求示例
curl -X POST "https://api.example.com/sms/send" \
  -d "sms_user=mycompany_sms" \
  -d "sms_key=xyz789uvw123" \
  -d "to=+1234567890" \
  -d "message=Hello World"
```
  </Tab>
</Tabs>

### 凭据管理

<Accordion title="获取和创建凭据" icon="mobile-alt">
**在哪里找到您的凭据：**

1. 登录您的账户
2. 从主菜单导航到 **Integrations** 页面
3. 在集成部分选择 **SMS Manage**
4. 访问 **Send Settings** 页面

**可用操作：**
- ➕ 添加新的 `SMS_USER`（遵循平台命名规范）
- 🔑 为用户生成关联的 `SMS_KEY`
- 🔄 重置现有的 `SMS_KEY`
</Accordion>

<Accordion title="即时重置机制" icon="bolt">
**重置SMS密钥时的机制：**

- ⚡ **立即生效**：新的 `SMS_KEY` 重置后立即生效
- ❌ **旧密钥失效**：旧密钥立即失效，没有宽限期
- 🚨 **需要立即更新**：必须立即更新集成配置以避免服务中断

**重置流程建议：**
```bash
# 1. 准备好更新脚本
# 2. 重置密钥
# 3. 立即更新配置
# 4. 马上测试新密钥
curl "https://api.example.com/sms/test?sms_user=youruser&sms_key=NEW_SMS_KEY"
```
</Accordion>

## 安全最佳实践

<Columns layout="auto">
  <Column>
### 🔐 凭据安全

- **环境变量存储**：将API密钥存储在环境变量中
- **定期轮换**：定期更换API密钥
- **最小权限**：为不同用途创建不同的API用户
- **监控使用**：定期检查API使用日志

```bash
# 推荐的环境变量设置
export EMAIL_API_USER="your_email_user"
export EMAIL_API_KEY="your_email_key"
export SMS_API_USER="your_sms_user"
export SMS_API_KEY="your_sms_key"
```
  </Column>
  <Column>
### 🛠️ 集成最佳实践

- **错误处理**：实现适当的认证错误处理
- **重试机制**：为认证失败添加重试逻辑
- **日志记录**：记录认证相关的事件（不记录密钥）
- **测试环境**：使用单独的测试凭据

```javascript
// 示例错误处理
if (response.status === 401) {
  console.error('认证失败，请检查API凭据');
  // 实现重试或报警逻辑
}
```
  </Column>
</Columns>

## 故障排除

<Accordion title="常见认证问题" icon="question-circle">
**🚫 认证失败 (401 Unauthorized)**
- 检查参数名称是否正确（`api_user`/`api_key` vs `sms_user`/`sms_key`）
- 确认凭据没有过期或被重置
- 验证参数值没有多余的空格或特殊字符

**⏱️ 密钥重置后无法访问**
- Email API：检查是否在15分钟宽限期内
- SMS API：确认已立即更新为新密钥

**📝 参数传递问题**
- 确保参数在请求体或查询字符串中，而非请求头
- 检查URL编码是否正确
- 验证POST请求的Content-Type设置
</Accordion>

<Accordion title="测试您的认证配置" icon="vial">
**快速测试脚本：**

```bash
#!/bin/bash
# Email API测试
echo "测试Email API认证..."
curl -s "https://api.example.com/email/test?api_user=$EMAIL_API_USER&api_key=$EMAIL_API_KEY"

echo -e "\n测试SMS API认证..."
curl -s "https://api.example.com/sms/test?sms_user=$SMS_API_USER&sms_key=$SMS_API_KEY"
```

**成功响应示例：**
```json
{
  "status": "success",
  "message": "Authentication successful",
  "user": "your_api_user"
}
```
</Accordion>

## 下一步

设置好身份验证后，您可以：

<Cards columns="3">
  <Card title="API 参考" href="/api-reference" icon="book">
    查看完整的API端点文档
  </Card>
  <Card title="快速开始" href="/getting-started" icon="play-circle">
    跟随我们的快速开始指南
  </Card>
  <Card title="SDK 文档" href="/sdks" icon="code">
    使用我们的官方SDK库
  </Card>
</Cards>

---

> 💡 **需要帮助？** 如果您在设置身份验证时遇到问题，请查看我们的[支持文档](/support)或联系技术支持团队。