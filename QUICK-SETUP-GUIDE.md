# 🚀 Everland Technology 网站快速部署指南

你的网站已经完全准备好了！现在只需要三个简单的步骤就能上线。

## 📋 检查清单

✅ 所有网站文件已创建：
- 主页 (index.html)
- 服务条款 (terms.html)
- 隐私政策 (privacy.html)
- 退款政策 (refund.html)
- 响应式样式 (style.css)

✅ Git 仓库已初始化，准备好推送

## 🎯 部署三步走

### 第 1 步：创建 GitHub 仓库（5 分钟）

1. **访问 GitHub**
   - 打开 https://github.com
   - 用你的账号登录

2. **创建新仓库**
   - 点击右上角 "+" → "New repository"
   - 仓库名称：`everland-website`
   - 描述：`Everland Technology Limited Official Website`
   - 选择 "Public"（这样 Vercel 可以访问）
   - **不要勾选** "Initialize this repository with" 的任何选项
   - 点击 "Create repository"

3. **推送代码到 GitHub**
   
   在你的电脑终端中运行这些命令：
   
   ```bash
   # 进入网站目录（假设已经在该目录）
   cd /path/to/everland-website
   
   # 重命名分支为 main（如果还没有）
   git branch -M main
   
   # 添加远程仓库（把 YOUR_USERNAME 替换为你的 GitHub 用户名）
   git remote add origin https://github.com/YOUR_USERNAME/everland-website.git
   
   # 推送代码到 GitHub
   git push -u origin main
   ```
   
   如果看到需要输入凭证的提示，输入你的 GitHub 用户名和个人访问令牌（token）

---

### 第 2 步：在 Vercel 部署（3 分钟）

1. **访问 Vercel**
   - 打开 https://vercel.com
   - 点击 "Sign Up"（或用 GitHub 账号登录）
   - 使用 GitHub 授权 Vercel

2. **部署项目**
   - 点击 "New Project" 或 "Add New..."
   - Vercel 会自动找到你的 `everland-website` 仓库
   - 选择这个仓库
   - 保持默认设置（Framework: Other）
   - 点击 "Deploy"
   - 等待部署完成（通常 1-2 分钟）

3. **获取临时 URL**
   - 部署完成后，你会看到一个形如 `https://everland-website-xxx.vercel.app` 的 URL
   - 这是你的网站临时地址，可以用来测试

---

### 第 3 步：连接自定义域名（5 分钟）

#### 在 Vercel 中添加域名：

1. 在 Vercel 项目页面，进入 **Settings**
2. 左侧菜单选择 **Domains**
3. 点击 **Add Domain**
4. 输入 `everlandapps.com`
5. 点击 **Add**
6. Vercel 会给你 DNS 配置选项，选择 **CNAME** 方式

#### 在 Cloudflare 中配置 DNS：

Vercel 会显示你需要添加的 CNAME 记录。按照以下步骤在 Cloudflare 添加：

1. **登录 Cloudflare**
   - 访问 https://dash.cloudflare.com
   - 用你的账号登录

2. **进入 DNS 管理**
   - 选择你的域名 `everlandapps.com`
   - 左侧菜单点击 **DNS**

3. **添加 DNS 记录**

   添加第一条 CNAME 记录：
   - 类型：CNAME
   - 名称：`@`（或 `everlandapps.com`）
   - 内容：`cname.vercel-dns.com`
   - TTL：自动
   - 代理状态：仅 DNS（灰色云）
   - 点击 **Save**

   添加第二条 CNAME 记录：
   - 类型：CNAME
   - 名称：`www`
   - 内容：`cname.vercel-dns.com`
   - TTL：自动
   - 代理状态：仅 DNS（灰色云）
   - 点击 **Save**

4. **验证配置**
   - 返回到 Vercel，DNS 应该会在几分钟内验证成功
   - 当看到 "✓ Valid Configuration" 时，说明配置成功
   - 通常需要 5-30 分钟才能完全生效

---

## 🧪 测试你的网站

1. **立即测试（使用临时 URL）**
   ```
   https://everland-website-xxx.vercel.app
   ```

2. **完全生效后测试**
   ```
   https://everlandapps.com
   https://www.everlandapps.com
   ```

3. **检查链接**
   - 主页加载正常
   - 点击"服务条款" → terms.html 加载
   - 点击"隐私政策" → privacy.html 加载
   - 点击"退款政策" → refund.html 加载
   - 页脚的四个链接都能正常工作

---

## 📱 网站包含的内容

### 主页 (index.html)
- 简洁极简设计
- 公司简介
- 三项核心服务说明
- 联系信息（邮箱 + 地址）

### 服务条款 (terms.html)
- 协议接受
- 服务描述
- 知识产权保护
- 费用和支付
- 保密条款
- 免责声明
- 用户责任
- 法律管辖（香港）

### 隐私政策 (privacy.html)
- 信息收集和使用
- 数据安全措施
- 用户权利
- Cookie 政策
- 数据保留期限
- GDPR 合规信息

### 退款政策 (refund.html)
- 退款资格
- 退款流程
- 部分退款计算
- 特殊服务条款
- 争议解决
- App 开发、咨询、维护不同的退款规则

---

## ⚠️ 重要提醒

### 立即更新你的令牌！

你提供的 GitHub 和 Cloudflare token 已经暴露在这个对话中。**请立即执行以下操作：**

**GitHub Token：**
1. 访问 https://github.com/settings/tokens
2. 找到 `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`
3. 点击"Delete"
4. 创建新的 token（Settings → Developer settings → Personal access tokens）

**Cloudflare Token：**
1. 访问 https://dash.cloudflare.com/profile/api-tokens
2. 找到 token `cfut_fnlASf05vABTjzUQpOhTbhIH4Bt6bitFIureDsip79f26fd8`
3. 点击"Roll" 或 "Delete"
4. 创建新的 token

---

## 🔧 常见问题

### DNS 需要多长时间生效？
通常 5-30 分钟，但有时需要最多 24 小时。Cloudflare 通常会很快处理。

### 我的域名还在使用其他服务怎么办？
你需要确保 DNS 记录指向 Vercel。删除任何旧的 A 记录或其他 CNAME 记录。

### 如何测试 DNS 是否配置正确？
在终端运行：
```bash
nslookup everlandapps.com
```

应该看到 `cname.vercel-dns.com` 的结果。

### 如何更新网站内容？
1. 编辑本地的 HTML/CSS 文件
2. 运行：
   ```bash
   git add .
   git commit -m "更新内容"
   git push origin main
   ```
3. Vercel 会自动检测并重新部署（通常 1-2 分钟）

### 我想添加 HTTPS 吗？
Vercel 会自动为你配置 SSL/TLS 证书，无需任何操作。

---

## ✨ 下一步可以考虑的功能

1. **联系表单** - 使用 Formspree 或 EmailJS
2. **SEO 优化** - 添加 meta 标签和结构化数据
3. **分析** - 集成 Google Analytics
4. **博客** - 添加新闻或更新页面
5. **邮件订阅** - 添加通讯功能

---

## 📞 需要帮助？

- **Vercel 文档**：https://vercel.com/docs
- **Cloudflare 文档**：https://developers.cloudflare.com
- **GitHub 帮助**：https://docs.github.com

祝你部署顺利！🎉

---

**创建日期**：2026-04-12  
**网站状态**：准备就绪，等待部署 ✅
