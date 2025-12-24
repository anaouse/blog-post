---
title: VitePress-Butterfly 主题 README
date: 2024-05-20
author: 57Darling02
---

# VitePress-Butterfly 主题

基于VitePress和Element Plus的卡片式仿butterfly主题。
结合obsidian成为**动态博客**方案！

##  功能

- 静态博客，不需要服务器也能有自己的个人网站
- vitepress完善的工作流自动构建，只需要首次配置
- vite的静态资源自动优化，不需要图床也能够插入图片
## 概览
将静态博客和文章分成两个仓库，一个用于博客仓库通过将文章仓库作为子模块引入文章。博客仓库负责博客网页样式配置等，而文章仓库仅仅用于存放要发布的文章。


## 法一：快速从零开始搭建一个博客

### 1.获取模板
分别fork下面两个项目到自己的仓库：

1. [57Darling02/blog-post(github.com)](https://github.com/57Darling02/blog-post)
2. [57Darling02/VitePress_butterfly(github.com)](https://github.com/57Darling02/VitePress_butterfly)

第一个用于存放文章，可以设为私密
第二个放网页源码，必须公开，推荐命名为`[你的GITHUB账号.github.io]`


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
在源码仓库中找到`site_config.ts`,对博客首页进行自定义配置。

将网站变成你的形状😤修改 site_config.ts进行主题配置信息，更改首页背景图、网站名称、侧边栏个人信息等等。
### 4.将文章仓库克隆到本地并写作

github进入文章仓库中，将其克隆到本地
例如：
```bash
git clone https://github.com/your-username/blog-post.git
cd blog-post
```

写出你的第一篇文章

```md
---
title: 文章标题
date: 2024-03-20
author: 作者
layout: doc # 这行不写也行，涉及到自定义页面才会涉及
---

# Hello World!
这是一篇文章，蛤蛤蛤！！！外币巴伯....

```


写完之后git上传到github即可。
推荐使用obsidian，可以直接在obsidian中将克隆下来的文章仓库打开，并利用第三方插件git更快速的修改文章。
> [!WARNING]
>  需要配置obsidian的内部链接类型为 相对位置


## 主题更新

在源码仓库中点击更新上游即可，注意保存配置文件`site_config.ts`

不定期修bug或更新新功能。

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

