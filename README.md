# 被讨厌的勇气 - 双语学习网站部署教程

## 📱 项目说明

这是一个基于 HTML + JavaScript 的静态网站，用于通过《被讨厌的勇气》这本书学习英语。网站针对手机端进行了优化。

## 🚀 部署方式

### 方式一：GitHub Pages（推荐，免费）

#### 1. 创建 GitHub 仓库

1. 登录 [GitHub](https://github.com)
2. 点击右上角 **+** → **New repository**
3. 仓库名填写：`courage-learning`
4. 选择 **Public**（公开）
5. 点击 **Create repository**

#### 2. 上传文件

```bash
# 进入项目目录
cd /Users/lily/Downloads/code/project/booklearner/courage/web

# 初始化 git
git init
git add .
git commit -m "Initial commit"

# 关联远程仓库（将 YOUR_USERNAME 替换为你的 GitHub 用户名）
git remote add origin https://github.com/YOUR_USERNAME/courage-learning.git
git branch -M main
git push -u origin main
```

#### 3. 启用 GitHub Pages

1. 进入仓库页面
2. 点击 **Settings** → **Pages**（左侧菜单）
3. **Source** 选择 **Deploy from a branch**
4. **Branch** 选择 **main** / **root**
5. 点击 **Save**

等待 1-2 分钟，访问 `https://YOUR_USERNAME.github.io/courage-learning`

---

### 方式二：Cloudflare Pages（推荐，国内访问更快）

#### 1. 注册 Cloudflare

访问 [cloudflare.com](https://cloudflare.com) 注册账号

#### 2. 创建 Pages 项目

1. 登录后点击 **Workers & Pages**
2. 点击 **Create application** → **Pages** → **Connect to Git**
3. 授权 GitHub 访问
4. 选择 `courage-learning` 仓库
5. 点击 **Begin setup**
6. **Build settings** 保持默认（静态网站不需要构建）
7. 点击 **Save and Deploy**

等待部署完成，Cloudflare 会提供一个 `*.pages.dev` 的域名

---

### 方式三：Netlify（推荐，拖拽部署）

#### 1. 打包文件

```bash
cd /Users/lily/Downloads/code/project/booklearner/courage/web
zip -r courage-learning.zip index.html content.json
```

#### 2. 部署到 Netlify

1. 访问 [netlify.com](https://netlify.com)
2. 注册/登录账号
3. 将 `courage-learning.zip` 拖拽到首页的虚线框区域
4. 等待部署完成，Netlify 会提供一个随机域名

#### 3. 自定义域名（可选）

1. 在 Netlify 项目页面点击 **Domain settings**
2. 点击 **Add custom domain**
3. 输入你的域名并按照提示配置 DNS

---

### 方式四：Vercel（推荐，国内访问快）

#### 1. 安装 Vercel CLI

```bash
npm install -g vercel
```

#### 2. 部署

```bash
cd /Users/lily/Downloads/code/project/booklearner/courage/web

# 登录（浏览器会弹出授权页面）
vercel login

# 部署
vercel --prod

# 按照提示操作：
# ? Set up and deploy? [Y/n] → Y
# ? Which scope? [选择你的账号]
# ? Link to existing project? [n]
# ? What’s your project name? [courage-learning]
```

部署完成后会显示访问地址

---

## 📋 文件结构

```
web/
├── index.html      # 网站主页面
├── content.json    # 中英文对话数据
└── README.md       # 本说明文件
```

## 🔧 更新网站内容

### 更新对话数据

如果你重新生成了 `content.json`，只需替换文件后重新部署：

**GitHub Pages:**
```bash
git add .
git commit -m "Update content"
git push origin main
```

**其他平台：** 直接重新上传或部署即可

## 🌐 自定义域名

### 绑定自己的域名

1. 在域名服务商（如阿里云、腾讯云、Namecheap 等）添加 DNS 记录：
   - 类型：CNAME
   - 主机记录：www（或你想用的子域名）
   - 记录值：你的 Pages 地址（如 `xxx.pages.dev` 或 `xxx.netlify.app`）

2. 在部署平台添加自定义域名

### 推荐免费域名

- [js.org](https://js.org) - 适合 JS 项目
- [eu.org](https://nic.eu.org) - 免费二级域名

## 🐛 常见问题

### 网站打开空白？

1. 检查 `content.json` 是否与 `index.html` 在同一目录
2. 浏览器控制台（F12）查看错误信息
3. 确保文件编码为 UTF-8

### 手机访问卡顿？

- 网站已针对手机优化，如果章节内容过多可能会卡顿
- 可以尝试分页加载（需要修改代码）

### 如何备份？

```bash
# 打包整个项目
cd /Users/lily/Downloads/code/project/booklearner/courage
tar -czvf courage-backup.tar.gz web/
```

## 💡 提示

- **推荐 Cloudflare Pages**：国内访问速度最快
- **推荐 GitHub Pages**：完全免费，配置简单
- 可以同时部署到多个平台，互为备份

## 📞 技术支持

如有问题，请检查：
1. 浏览器开发者工具控制台（F12）
2. 网络请求是否正常
3. JSON 文件格式是否正确

---

**祝你学习愉快！** 📚
