# ✅ Everland Technology 网站 - 部署检查清单

## 📦 当前状态

### ✅ 已完成
- [x] 网站主页 (index.html)
- [x] 服务条款页面 (terms.html)
- [x] 隐私政策页面 (privacy.html)
- [x] 退款政策页面 (refund.html)
- [x] 响应式样式表 (style.css)
- [x] Vercel 部署配置 (vercel.json)
- [x] Git 仓库初始化
- [x] 完整部署指南
- [x] 快速设置指南
- [x] 命令参考卡

### ⏳ 需要你完成

## 第 1 步：推送代码到 GitHub

**时间预计**：5 分钟

### 前置条件检查：
- [ ] 你有 GitHub 账号（没有的话 https://github.com/join）
- [ ] 你有 GitHub 个人访问令牌（PAT）
- [ ] 你已安装 Git 命令行工具

### 执行步骤：

```bash
# 1. 进入网站文件夹
cd /path/to/everland-website

# 2. 创建 GitHub 仓库（https://github.com/new）
# 仓库名：everland-website
# 可见性：Public

# 3. 配置 Git 远程仓库（替换 YOUR_USERNAME）
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/everland-website.git

# 4. 推送代码
git push -u origin main
```

### 验证：
- [ ] 代码推送成功（看到 "refs/heads/main" 消息）
- [ ] 访问 https://github.com/YOUR_USERNAME/everland-website 能看到代码
- [ ] 所有 5 个 HTML 文件都在仓库中
- [ ] style.css 在仓库中

---

## 第 2 步：部署到 Vercel

**时间预计**：3 分钟

### 执行步骤：

1. [ ] 访问 https://vercel.com
2. [ ] 点击"Sign Up"或用 GitHub 登录
3. [ ] 授权 Vercel 访问你的 GitHub 账号
4. [ ] 点击"New Project"
5. [ ] Vercel 会自动找到你的仓库列表
6. [ ] [ ] 选择 "everland-website"
7. [ ] 保持默认设置（无需修改）
8. [ ] 点击"Deploy"
9. [ ] 等待部署完成（1-2 分钟）

### 验证：
- [ ] Vercel 显示 "Deployment Ready"
- [ ] 你获得了一个形如 `everland-website-xxx.vercel.app` 的临时 URL
- [ ] 访问该 URL，网站能正常显示
- [ ] 四个页面都能正常加载：
  - [ ] 首页 (/)
  - [ ] 服务条款 (/terms.html)
  - [ ] 隐私政策 (/privacy.html)
  - [ ] 退款政策 (/refund.html)

---

## 第 3 步：配置自定义域名

**时间预计**：5 分钟

### 在 Vercel 中添加域名：

1. [ ] 进入你的 Vercel 项目页面
2. [ ] 点击"Settings"（左侧菜单）
3. [ ] 选择"Domains"
4. [ ] 点击"Add Domain"
5. [ ] 输入 `everlandapps.com`
6. [ ] 点击"Add"
7. [ ] Vercel 会显示 DNS 配置选项
8. [ ] 选择"CNAME"方式（最简单）

### 在 Cloudflare 中添加 DNS 记录：

1. [ ] 访问 https://dash.cloudflare.com
2. [ ] 登录你的 Cloudflare 账号
3. [ ] 选择域名 `everlandapps.com`
4. [ ] 左侧菜单选择"DNS"

#### 添加第一条记录：
- [ ] 点击"Add record"
- [ ] 类型：CNAME
- [ ] 名称：@ （或 everlandapps.com）
- [ ] 内容：`cname.vercel-dns.com`
- [ ] TTL：Auto
- [ ] 代理状态：DNS only（灰色云）
- [ ] 点击"Save"

#### 添加第二条记录：
- [ ] 点击"Add record"
- [ ] 类型：CNAME
- [ ] 名称：www
- [ ] 内容：`cname.vercel-dns.com`
- [ ] TTL：Auto
- [ ] 代理状态：DNS only（灰色云）
- [ ] 点击"Save"

### 验证 DNS 配置：

在你的电脑终端运行：
```bash
nslookup everlandapps.com
```

结果中应该包含：
```
everlandapps.com    CNAME   cname.vercel-dns.com
```

- [ ] DNS 查询返回正确的 CNAME 记录

---

## 第 4 步：验证完整部署

**时间预计**：5 分钟（等待 DNS 传播）

### DNS 传播检查：

DNS 通常需要 5-30 分钟完全生效。可以用以下工具检查：

- [ ] https://dnschecker.org/ - 输入 "everlandapps.com"
- [ ] 检查 Vercel 部署日志中的 DNS 验证状态
- [ ] Vercel 显示 "✓ Valid Configuration"

### 网站访问测试：

一旦 DNS 生效，测试以下 URL：

- [ ] https://everlandapps.com （可能需要等待几分钟）
- [ ] https://www.everlandapps.com
- [ ] https://everlandapps.com/terms.html
- [ ] https://everlandapps.com/privacy.html
- [ ] https://everlandapps.com/refund.html

### 功能验证：

- [ ] 页面加载速度正常
- [ ] 页脚的 4 个链接都能点击
- [ ] 联系信息显示正确
  - [ ] admin@everlandapps.com
  - [ ] 地址信息完整
- [ ] 在手机上测试网站响应式
  - [ ] 导航菜单正常
  - [ ] 文本可读
  - [ ] 链接可点击

### HTTPS 检查：

- [ ] URL 显示 "https://" 而不是 "http://"
- [ ] 浏览器地址栏显示绿色锁图标
- [ ] 没有任何安全警告

---

## ⚠️ 安全检查项

**必须完成：**

- [ ] ❌ **删除/更新暴露的 GitHub Token**
  - 访问：https://github.com/settings/tokens
  - 找到并删除/重新生成 token

- [ ] ❌ **删除/更新暴露的 Cloudflare Token**
  - 访问：https://dash.cloudflare.com/profile/api-tokens
  - 找到并删除/重新生成 token

这些 token 已经在对话中显示过，为了安全起见必须立即更新！

---

## 🧪 额外测试

### 页面加载时间（可选）
使用以下工具检查网站性能：
- [ ] https://pagespeed.web.dev/
- [ ] 输入 `everlandapps.com`
- [ ] 查看 Lighthouse 评分
- [ ] 记录加载时间

### SEO 基础检查（可选）
- [ ] https://www.seobility.net/
- [ ] 分析 SEO 评分
- [ ] 检查 meta 标签

### 跨浏览器测试（可选）
- [ ] Chrome/Edge
- [ ] Firefox
- [ ] Safari
- [ ] 移动浏览器

---

## 📊 最终验证清单

全部检查完毕后，勾选下面的项目：

### 功能完整性
- [ ] 所有 4 个页面都能访问
- [ ] 所有链接都能工作
- [ ] 没有 404 错误
- [ ] 没有样式错误

### 性能指标
- [ ] 页面加载时间 < 3 秒
- [ ] Lighthouse 评分 > 80
- [ ] 移动端可用性正常

### 安全合规
- [ ] HTTPS 启用
- [ ] 没有混合内容警告
- [ ] 隐私政策页面可访问
- [ ] 服务条款页面可访问

### DNS 和域名
- [ ] everlandapps.com 指向 Vercel
- [ ] www.everlandapps.com 指向 Vercel
- [ ] DNS 验证完成 (Vercel Dashboard)
- [ ] SSL 证书配置完成

---

## ✨ 部署完成！

如果你已经勾选了上面的所有项目，那么恭喜你！🎉

你的 Everland Technology 官方网站现在已经：
- ✅ 部署到 Vercel
- ✅ 连接到自定义域名 everlandapps.com
- ✅ 配置了 DNS 和 SSL
- ✅ 包含完整的法律政策
- ✅ 在全球范围内通过 CDN 加速

---

## 📞 后续支持

### 需要修改网站？
1. 编辑 HTML 文件
2. 推送到 GitHub：`git push origin main`
3. Vercel 会自动重新部署

### 遇到问题？
参考这些文件：
- **QUICK-SETUP-GUIDE.md** - 快速参考
- **DEPLOYMENT.md** - 完整技术文档
- **COMMANDS.txt** - 命令参考

### 有问题需要帮助？
联系 admin@everlandapps.com

---

**清单创建日期**：2026-04-12  
**预计完成时间**：15-20 分钟  
**难度等级**：⭐⭐ 简单

祝你的网站成功上线！🚀
