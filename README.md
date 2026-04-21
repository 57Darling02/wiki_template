---
title: VitePress-Butterfly 主题 README
date: 2024-05-20
author: 57Darling02
layout: doc
---

# VitePress-Butterfly 主题

基于VitePress和Element Plus的卡片式仿butterfly主题。
结合obsidian成为**动态博客**方案！

##  功能

- 静态博客，不需要服务器也能有自己的个人网站
- vitepress完善的工作流自动构建，只需要首次配置
- vite的静态资源自动优化，不需要图床也能够插入图片

## 概览


## 法一：快速从零开始搭建一个博客

### 1.获取模板
分别将下面两个模板项目fork到自己的仓库：

1. [57Darling02/blog-post(github.com)](https://github.com/57Darling02/blog-post)
2. [57Darling02/VitePress_butterfly(github.com)](https://github.com/57Darling02/VitePress_butterfly)


第一个用于存放文章，可以设为私密
第二个放网页源码，必须公开，推荐命名为`[你的GITHUB账号.github.io]`
![](附件/Pasted%20image%2020251225014512.png)

### 2.配置变量

##### 创建 GitHub 个人访问令牌（PAT）

1. 打开 GitHub → 右上角头像 → `Settings` → `Developer settings` → `Personal access tokens` → `Tokens (classic)`；
2. 点击 `Generate new token (classic)`；
3. 配置：
    - `Note`：填 `blog-access`；
    - `Expiration`：选 `No expiration`（或按需设置）；
    - `Scopes`：勾选 `repo`（全选 repo 相关权限）；
4. 点击 `Generate token`，**复制生成的 Token（只显示一次，务必保存）**。
##### 配置两个仓库的PAT和相关变量
##### 将 PAT 添加到仓库的 Secrets

1. 仓库 → `Settings` → `Secrets and variables` → `Actions` → `New repository secret`；
2. `Name`：填 `PERSONAL_ACCESS_TOKEN`；
3. `Value`：粘贴生成的 PAT；
4. 点击 `Add secret`。

两个仓库中都添加键值对
`PERSONAL_ACCESS_TOKEN` 为键，对应值为 生成的PAT

另外，在文章仓库中添加：
`BLOG_REPO`为键，对应值为 "用户名/源码仓库" 如：
`[你的GITHUB账号]/[你的GITHUB账号].github.io`
或者
`57Darling02/VitePress_butterfly

在源码仓库中添加：
`POST_REPO`为键，对应值为 "文章仓库链接" 如：
`https://github.com/57Darling02/blog-post.git`

### 3.修改博客配置
在源码仓库中找到`site_config.ts`,copy一份到你的文章仓库，在修改`site_config.ts`对博客首页进行自定义配置。
> 文章仓库的`site_config.ts`会优先起作用

将网站变成你的形状😤修改 site_config.ts进行主题配置信息，更改首页背景图、网站名称、侧边栏个人信息等等。



github page中改变部署来源为 action

### 4.将文章仓库克隆到本地并写作

github进入文章仓库中，将其克隆到本地
例如：
```bash
git clone https://github.com/your-username/blog-post.git
cd blog-post
```

写出你的第一篇文章

> [!Notice]
> 只有配置了`layout: doc`才会发布在博客
> 这意味着如果你不希望公开一篇博文，只要没有`layout: doc`即可
```md
---
title: 文章标题
date: 2024-03-20
author: 作者
layout: doc
---

# Hello World!
这是一篇文章，蛤蛤蛤！！！外币巴伯....

```


写完之后git上传到github即可。
推荐使用obsidian，可以直接在obsidian中将克隆下来的文章仓库打开，并利用第三方插件git更快速的修改文章。

> [!WARNING]
>  需要配置obsidian的内部链接类型
>   **相对位置**，调整 **附件位置**
>  **不使用WiKi链接**

********
![](附件/Pasted%20image%2020251225154231.png)




### 自定义域名
完成之前的步骤后，`[你的GITHUB账号]/[你的GITHUB账号].github.io`这个域名应该已经可用。但是如果你希望使用自己的域名，下面提供了两个方法。

1. 使用github直接自定义域名。很方便不需要其他配置。
>[!WARNING]
>如果需要使用github托管多个静态网页，这种方法无法绑定多个域名。
2. 使用vercel+github action,唯一缺点就是需要为vercel额外配置一些参数。



#### 1.直接用github
配置域名
![](附件/Pasted%20image%2020251225014856.png)
将域名的DNS指向github提供的服务器IP，具体IP请看：
[管理 GitHub Pages 站点的自定义域 - GitHub 文档](https://docs.github.com/zh/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

> [!TIPS]
> 虽然文档中写顶级域名才直接用AAAA或者A记录，子域需要用CNAME，但如果你只有一个github page，那么直接给子域名添加A或AAAA记录也没问题。




#### 2.Vercel部署
如果要部署的网页不止一个，那么你的github page就无法将不同的页面映射到不同的域名上。此时需要借助vercel部署。

模板的workflow中还有一个`vercel.yml`，还需要额外配置三个参数。
`VERCEL_ORG_ID` `VERCEL_PROJECT_ID` `VERCEL_TOKEN`


[Two Ways to Find Vercel ORG_ID and PROJECT_ID (codenote.net)](https://codenote.net/en/posts/how-to-find-vercel-org-project-ids/)
简单来说：
1. 在vercel中配置token
2. 关联github仓库
3. 获取`Project ID` 和`Team ID`
	并将它们分别配置为`VERCEL_TOKEN` `VERCEL_TOKEN`和`VERCEL_ORG_ID`
## 主题更新

在源码仓库中点击更新上游即可


或者使用命令行，打开源码仓库终端执行

```bash
git remote add upstream https://github.com/57Darling02/VitePress_butterfly.git

git fetch upstream && git checkout main && git reset --hard upstream/main && git push origin main --force
```


### 目录结构

```plainText
Blog/                   # 项目根目录
├── .vitepress/         # 主题组件 不会为这部分提供文档 (一般不用动)
│   ├── theme/
│   ├── site_config.ts  # 模板文件，可以复制到根目录下修改使用          
│   ├── config.mjs   
│   ├── index.js
│   └── ...   
├── site_config.ts     # 站点配置 自定义的配置，主要修改这个文件来配置站点信息
├── posts/             # Markdown文章
├── public/            # 静态资源 例如背景图片，例如 public/a.png 则配置中对应 /a.png
└── package.json       # 依赖配置 (一般不用动)
```
### 文章规范

```markdown
---
title: 文章标题
date: 2024-03-20
author: 作者
cover: url... 
layout: doc # 可选布局
---
```
贡献
欢迎贡献代码和反馈问题。

