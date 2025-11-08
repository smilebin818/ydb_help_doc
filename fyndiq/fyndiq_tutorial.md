# Fyndiq JWT Token 获取教程

本教程将指导您如何从 Fyndiq 商家后台获取 JWT Token，并将其配置到易店邦软件中。

---

## 📋 为什么要做去获取JWT信息
我们要去同步平台的产品状态为[已被锁 或者 已暂停]的产品. 目前平台没有提供API接口, 
所以暂时只能模拟用户登录到平台后台, 进行检索对应的状态的产品 获取到这2个状态的产品

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
<img width="834" height="551" alt="image" src="https://github.com/user-attachments/assets/4fed9074-b981-43d4-8566-49acc4383ab1" />

---

### 步骤 2：打开浏览器开发者工具

**在打开的 Fyndiq 页面上，按 `F12` 键：

开发者工具会在浏览器底部或右侧打开。

### 步骤 3：切换到 Network 标签页

1. 在开发者工具顶部找到 **"Network"**（网络）标签
2. 点击切换到 Network 标签页
<img width="1216" height="643" alt="image" src="https://github.com/user-attachments/assets/eafcfcc3-725b-4177-896f-72918d73b621" />

> ⚠️ **重要提示**：请在登录之前先打开开发者工具，这样才能捕获到登录请求。

---

### 步骤 4：登录您的 Fyndiq 账号

1. 在 Fyndiq 登录页面输入您的商家账号和密码
2. 点击"登录"按钮
3. 等待登录成功，页面跳转到商家后台主页

**此时，开发者工具的 Network 标签会捕获所有网络请求。**

<img width="1222" height="634" alt="image" src="https://github.com/user-attachments/assets/f43cd8c7-d4fe-4fc0-b6cf-18b3fdfd1f46" />


---

### 步骤 5：查找 JWT Token

1. 在 Network 标签页中，按 `Ctrl + F`打开搜索框
2. 在搜索框中输入：`jwt`
3. 浏览器会高亮显示所有包含"jwt"的请求

<img width="1219" height="637" alt="image" src="https://github.com/user-attachments/assets/d2fb764b-f8d2-459c-a4be-04242c827ec9" />


---

### 步骤 6：定位 JWT Token

在搜索结果中，找到与登录相关的请求（通常是 `auth` 相关的请求）：

1. 点击该请求
2. 在右侧面板中，切换到 **"Headers"**（请求头）标签
3. 向下滚动找到 **"Response Headers"**（响应头）部分
4. 找到 `set-cookie` 字段
5. 在 `set-cookie` 中找到以 `jwt=` 开头的那一行

JWT Token 的格式类似：
```
jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhdXRoZW50aWNhdGlvbi1zZXJ2aWNlIi...
```

<img width="1919" height="865" alt="image" src="https://github.com/user-attachments/assets/2f9b3486-5230-40b6-8927-4c6cd09e8af6" />

---

### 步骤 7：复制 JWT Token

1. **完整复制 JWT 值**（从 `eyJ` 开始，到分号 `;` 之前）
2. JWT Token 通常很长，确保完整复制，不要遗漏任何字符

> 💡 **提示**：右键点击该行，选择"Copy value"（复制值）可以快速复制整个 JWT Token。

---

### 步骤 8：配置到易店邦软件

1. 打开易店邦软件
2. 进入 Fyndiq 店铺管理页面
3. 选中你要同步[已被锁, 已暂停]的店铺, 然后点击[编辑店铺]

   <img width="319" height="264" alt="image" src="https://github.com/user-attachments/assets/62662021-2bfe-4919-9892-b87fc1654a8e" />

4. 将复制的 JWT Token 粘贴到输入框中
   
   <img width="363" height="334" alt="image" src="https://github.com/user-attachments/assets/f6ab1a2f-fdf9-4906-a409-053f82ab79d4" />
   
9. 点击"更新"按钮

---

## ✅ 验证配置

配置完成后，我们就可以选中去同步[已被锁 或者 已暂停]的产品信息了

### 1. JWT Token 无效或过期？

**解决方案**：
- JWT Token 通常有效期为 1 小时
- Token 过期后需要重新登录获取新的 Token

### 2. 复制的 Token 不完整？

**解决方案**：
- JWT Token 由三部分组成，用 `.` 分隔，确保三部分都复制完整
- 格式应为：`xxxxx.yyyyy.zzzzz`
- 避免复制到额外的空格或换行符

---

## 🔒 安全提示

- ⚠️ **不要将 JWT Token 分享给他人**，它相当于您的登录凭证
- ⚠️ **不要在公共场合展示 JWT Token**
- ⚠️ **定期更换 Token**，建议每次使用后重新获取
- ⚠️ JWT Token 可以访问您的商家账号数据，请妥善保管

---

## 📞 需要帮助？

如果您在获取 JWT Token 过程中遇到任何问题，请联系易店邦客服支持：

