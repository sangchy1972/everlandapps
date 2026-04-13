# Everland Technology 网站部署指南

## 项目概述
这是 Everland Technology Limited 的官方网站，包含公司简介、服务列表、以及完整的法律政策文件（Terms of Service、Privacy Policy、Refund Policy）。

## 文件结构
```
.
├── index.html          # 主页面（公司简介、服务、联系方式）
├── terms.html          # 服务条款页面
├── privacy.html        # 隐私政策页面
├── refund.html         # 退款政策页面
├── style.css           # 统一样式文件（简洁极简风格）
├── package.json        # Node.js 包配置
├── vercel.json         # Vercel 部署配置
├── .gitignore          # Git 忽略文件
└── DEPLOYMENT.md       # 本部署指南
```

## 部署步骤

### 第一步：准备 GitHub 仓库
1. 在 GitHub 创建新仓库：`everland-website`
2. 在本地初始化 Git：
   ```bash
   cd 项目目录
   git init
   git add .
   git commit -m "Initial commit: Everland Technology website"
   git branch -M main
   git remote add origin https://github.com/你的用户名/everland-website.git
   git push -u origin main
   ```

### 第二步：在 Vercel 部署
1. 访问 [Vercel](https://vercel.com)
2. 用 GitHub 账户登录
3. 点击"New Project"
4. 选择 `everland-website` 仓库
5. 保持默认设置（Framework: Other，Output Directory: 默认）
6. 点击"Deploy"
7. 等待部署完成（通常 1-2 分钟）

### 第三步：添加自定义域名
在 Vercel 项目中：
1. 进入 Project Settings
2. 导航到 "Domains"
3. 点击 "Add Domain"
4. 输入 `everlandapps.com`
5. 选择 "Use Nameservers" 或 "CNAME" 方式（见下一步）

### 第四步：在 Cloudflare 配置 DNS
在您的 Cloudflare 账户中：

#### 如果选择 CNAME 方式：
1. 登录 Cloudflare 控制面板
2. 选择 `everlandapps.com` 域名
3. 进入 DNS 管理
4. 添加以下 DNS 记录：

   **对于主域名 (@/root)：**
   - 类型：CNAME
   - 名称：@（或 everlandapps.com）
   - 内容：cname.vercel-dns.com
   - TTL：自动
   - 代理状态：仅 DNS

   **对于 www 子域名：**
   - 类型：CNAME
   - 名称：www
   - 内容：cname.vercel-dns.com
   - TTL：自动
   - 代理状态：仅 DNS

   **如果您想要 A 记录（Vercel IPv4）：**
   - 类型：A
   - 名称：@
   - 内容：76.76.19.89
   - TTL：自动
   - 代理状态：仅 DNS

#### 如果选择使用 Vercel 名称服务器：
1. Vercel 会提供两个名称服务器 (NS) 地址
2. 在 Cloudflare 中：
   - 进入 Domain Settings → Nameservers
   - 更改为 Vercel 提供的名称服务器
   - 保存更改

### 第五步：验证 DNS 配置
1. 在 Cloudflare 中，等待 DNS 更改传播（通常 24 小时，但通常在几分钟内生效）
2. 使用 nslookup 或 dig 命令验证：
   ```bash
   nslookup everlandapps.com
   ```
3. 访问 `https://everlandapps.com` 验证网站是否正常加载
4. 在 Vercel 项目中，查看"Domains"选项卡，状态应显示"✓ Valid Configuration"

### 第六步：启用 HTTPS（自动）
- Vercel 会自动为您的域名配置 SSL/TLS 证书（通过 Let's Encrypt）
- 此过程通常需要几分钟到 24 小时

## DNS 记录参考

### 最简单的方式（推荐用于 Vercel）：
| 类型 | 名称 | 内容 | TTL |
|------|------|------|-----|
| CNAME | @ | cname.vercel-dns.com | 自动 |
| CNAME | www | cname.vercel-dns.com | 自动 |

### 使用 A 记录：
| 类型 | 名称 | 内容 | TTL |
|------|------|------|-----|
| A | @ | 76.76.19.89 | 自动 |
| CNAME | www | cname.vercel-dns.com | 自动 |

## 网站内容清单
✓ 主页 (index.html)
  - 公司简介
  - 服务列表（App开发、信息咨询、定制解决方案）
  - 联系信息（邮箱和地址）

✓ 服务条款 (terms.html)
  - 适用于 App 开发和咨询服务

✓ 隐私政策 (privacy.html)
  - 包含数据保护和 Cookie 政策

✓ 退款政策 (refund.html)
  - 覆盖所有服务类型的退款条款

## 进一步自定义建议
1. **添加联系表单** - 使用 Formspree、EmailJS 或类似服务
2. **SEO 优化** - 添加元标签、结构化数据（Schema.org）
3. **分析** - 集成 Google Analytics 或类似工具
4. **社交媒体链接** - 在页脚添加链接
5. **多语言支持** - 如果需要英文版本

## 常见问题

### DNS 变更需要多长时间生效？
DNS 更改通常需要 24 小时完全传播，但通常在几分钟内就可以工作。

### 如何更新网站内容？
1. 在本地编辑 HTML/CSS 文件
2. 提交到 Git：`git add . && git commit -m "Update" && git push`
3. Vercel 会自动检测更改并重新部署

### 如何测试网站？
- Vercel 会为每个部署提供一个临时 URL（形如 `https://everlandapps-xxx.vercel.app`）
- 在添加自定义域名前可以使用此 URL 测试

### 我想添加 API 或后端功能？
- Vercel 支持 Serverless Functions
- 可以创建 `/api` 目录来添加服务器端代码

## 支持和维护
- 定期备份您的网站文件
- 监控 Vercel 仪表板的任何错误或警告
- 保持域名和 SSL 证书最新

## 许可证
Proprietary - Everland Technology Limited © 2026
