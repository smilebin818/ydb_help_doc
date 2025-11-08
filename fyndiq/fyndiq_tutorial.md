# Fyndiq JWT Token 获取教程

本教程将指导您如何从 Fyndiq 商家后台获取 JWT Token，并将其配置到易店邦软件中。

---

## 📋 前提条件

- 拥有 Fyndiq 商家账号
- 已安装 Chrome、Edge 或 Firefox 浏览器
- 已安装易店邦软件

---

## 🔧 详细步骤

### 步骤 1：打开 Fyndiq 商家后台

1. 打开浏览器
2. 访问 Fyndiq 商家中心：[https://merchantcenter.fyndiq.se/](https://merchantcenter.fyndiq.se/)

![打开商家后台](https://via.placeholder.com/800x400?text=Step+1:+Open+Fyndiq+Merchant+Center)

---

### 步骤 2：打开浏览器开发者工具

**在打开的 Fyndiq 页面上，按 `F12` 键**（或使用以下方式之一）：

- **Windows/Linux**: `F12` 或 `Ctrl + Shift + I`
- **Mac**: `Cmd + Option + I`
- **右键菜单**: 右键点击页面 → 选择"检查"或"Inspect"

开发者工具会在浏览器底部或右侧打开。

![开发者工具](https://via.placeholder.com/800x400?text=Step+2:+Open+DevTools+(F12))

> ⚠️ **重要提示**：请在登录之前先打开开发者工具，这样才能捕获到登录请求。

---

### 步骤 3：切换到 Network 标签页

1. 在开发者工具顶部找到 **"Network"**（网络）标签
2. 点击切换到 Network 标签页
3. 确保网络记录功能已启用（左上角的红色圆点应该是实心的）

![Network 标签](https://via.placeholder.com/800x400?text=Step+3:+Switch+to+Network+Tab)

---

### 步骤 4：登录您的 Fyndiq 账号

1. 在 Fyndiq 登录页面输入您的商家账号和密码
2. 点击"登录"按钮
3. 等待登录成功，页面跳转到商家后台主页

**此时，开发者工具的 Network 标签会捕获所有网络请求。**

![登录账号](https://via.placeholder.com/800x400?text=Step+4:+Login+to+Fyndiq)

---

### 步骤 5：查找 JWT Token

1. 在 Network 标签页中，按 `Ctrl + F`（Mac: `Cmd + F`）打开搜索框
2. 在搜索框中输入：`jwt`
3. 浏览器会高亮显示所有包含"jwt"的请求

![搜索 JWT](https://via.placeholder.com/800x400?text=Step+5:+Search+for+JWT)

---

### 步骤 6：定位 JWT Token

在搜索结果中，找到与登录相关的请求（通常是 `login`、`auth` 或 `session` 相关的请求）：

1. 点击该请求
2. 在右侧面板中，切换到 **"Headers"**（请求头）标签
3. 向下滚动找到 **"Response Headers"**（响应头）部分
4. 找到 `set-cookie` 字段
5. 在 `set-cookie` 中找到以 `jwt=` 开头的那一行

JWT Token 的格式类似：
```
jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhdXRoZW50aWNhdGlvbi1zZXJ2aWNlIi...
```

![定位 JWT](https://via.placeholder.com/800x400?text=Step+6:+Locate+JWT+Token)

---

### 步骤 7：复制 JWT Token

1. **完整复制 JWT 值**（从 `eyJ` 开始，到分号 `;` 之前）
2. JWT Token 通常很长，确保完整复制，不要遗漏任何字符

**示例：**
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhdXRoZW50aWNhdGlvbi1zZXJ2aWNlIiwiYXVkIjpbIm1lcmNoYW50LWFwaS1nYXRld2F5Il0sInN1YiI6IjQxMDRhZWY0LWUzMDQtNDYzMi04ODJjLTk5YmVlOGYzZTAzMCIsImlhdCI6MTc2MjUwMTg3NSwiZXhwIjoxNzYyNTA1NDc1LCJtZXJjaGFudF9pZCI6IjQ0ZjAzMzJhLTZlNmItNDg5Yy1hZWM0LTliM2Y0ZTJlMjU2MSIsInVzZXJuYW1lIjoiNDRmMDMzMmEtNmU2Yi00ODljLWFlYzQtOWIzZjRlMmUyNTYxIiwibmFtZSI6IkFkbWluIiwicGVybWlzc2lvbnMiOlsiYXJ0aWNsZS5jcmVhdGUiLCJhcnRpY2xlLmRlbGV0ZSIsImFydGljbGUuZ2V0IiwiYXJ0aWNsZS5saXN0IiwiYXJ0aWNsZS5tb2RlcmF0aW9uLmNyZWF0ZSIsImFydGljbGUubW9kZXJhdGlvbi5saXN0IiwiYXJ0aWNsZS51cGRhdGUiLCJjYXRlZ29yeS5saXN0IiwibWVyY2hhbnQuZ2V0IiwibWVyY2hhbnQudXBkYXRlIiwibWVyY2hhbnQudXNlci5saXN0Iiwib3JkZXIuY3JlYXRlIiwib3JkZXIuZ2V0Iiwib3JkZXIubGlzdCIsIm9yZGVyLnVwZGF0ZSIsInJlcG9ydC5maW5hbmNlLmdldCIsInJlcG9ydC5maW5hbmNlLmxpc3QiXSwicmF0ZV9saW1pdHMiOm51bGwsIm1heF9hcnRpY2xlc19saW1pdCI6NDAwMDAsImFsbG93ZWRfbWFya2V0cyI6WyJTRSIsIkZJIl19.keGajtBgbu5ZG1sOKvVnObsw1duLXSh_QRK5IkyA7W4
```

> 💡 **提示**：右键点击该行，选择"Copy value"（复制值）可以快速复制整个 JWT Token。

---

### 步骤 8：配置到易店邦软件

1. 打开易店邦软件
2. 进入 Fyndiq 平台配置页面
3. 找到 "JWT Token" 或 "授权令牌" 输入框
4. 将复制的 JWT Token 粘贴到输入框中
5. 点击"保存"或"验证"按钮

![配置到易店邦](https://via.placeholder.com/800x400?text=Step+8:+Configure+in+Software)

---

## ✅ 验证配置

配置完成后，易店邦软件会自动验证 JWT Token 的有效性：

- ✅ **验证成功**：显示绿色提示，可以开始使用
- ❌ **验证失败**：请检查 Token 是否完整复制，或重新获取

---

## ⚠️ 常见问题

### 1. 找不到 JWT Token？

**解决方案**：
- 确保在登录**之前**打开了开发者工具
- 尝试清除浏览器缓存后重新登录
- 检查是否在 Cookies 标签中（Application → Cookies → https://merchantcenter.fyndiq.se）

### 2. JWT Token 无效或过期？

**解决方案**：
- JWT Token 通常有效期为 1-24 小时
- Token 过期后需要重新登录获取新的 Token
- 建议在易店邦软件中启用"自动刷新"功能（如果有）

### 3. 复制的 Token 不完整？

**解决方案**：
- JWT Token 由三部分组成，用 `.` 分隔，确保三部分都复制完整
- 格式应为：`xxxxx.yyyyy.zzzzz`
- 避免复制到额外的空格或换行符

### 4. 在 Network 中搜索不到 jwt？

**解决方案**：
- 尝试在 **Application** → **Cookies** 中查找
- 选择 `https://merchantcenter.fyndiq.se` 域名
- 找到名为 `jwt` 的 Cookie
- 复制其值

---

## 🔒 安全提示

- ⚠️ **不要将 JWT Token 分享给他人**，它相当于您的登录凭证
- ⚠️ **不要在公共场合展示 JWT Token**
- ⚠️ **定期更换 Token**，建议每次使用后重新获取
- ⚠️ JWT Token 可以访问您的商家账号数据，请妥善保管

---

## 📞 需要帮助？

如果您在获取 JWT Token 过程中遇到任何问题，请联系易店邦客服支持：

- 📧 邮箱：support@yidianbang.com
- 💬 在线客服：[联系我们](https://www.yidianbang.com/support)
- 📱 客服电话：400-XXX-XXXX

---

## 📝 更新日志

- **v1.0** (2024-11-08) - 初始版本发布

---

*本教程由易店邦技术团队提供 | 最后更新：2024年11月*