# Blog 发布说明

## 概述

个人技术博客正式上线，基于 **Hugo** 与 **PaperMod** 主题构建，托管于 **GitHub Pages**。

- **站点**: [jacvan.dev](https://jacvan.dev/)
- **作者**: Jacky
- **定位**: 技术笔记 · 项目分享 · 成长记录

---

## 技术栈

| 组件       | 选型                 |
|------------|----------------------|
| 静态站点   | Hugo 0.146.0+        |
| 主题       | PaperMod             |
| 评论系统   | Giscus (GitHub Discussions) |
| 部署       | GitHub Actions → GitHub Pages |
| 构建优化   | `--gc --minify`      |

---

## 功能特性

### 内容与排版

- Markdown 写作，Front Matter 元数据管理
- 草稿 / 发布 工作流
- 封面图与摘要
- 代码高亮、复制按钮
- 文章内目录 (TOC)
- 阅读时间估算

### 导航与发现

- 首页文章列表、分页
- 分类 (Categories) 与标签 (Tags)
- 归档 (Archives)
- 全文搜索 (Fuse.js)

### 交互与展示

- 深色 / 浅色 / 跟随系统主题
- 分享按钮
- RSS 订阅 (`/index.xml`)
- Giscus 评论（基于 GitHub Discussions）

### 部署

- CI/CD：push 到 `main` 分支自动构建与部署
- 支持 `workflow_dispatch` 手动触发
- 使用 `actions/deploy-pages@v4` 部署到 GitHub Pages

---

## 内容结构

```
content/
├── about.md          # 关于页
├── archives.md       # 归档页
├── search.md         # 搜索页
└── posts/            # 文章目录
    ├── 2025-01-25-my-first-blog.md
    ├── 2025-02-01-two-weeks-summary.md
    ├── 2025-02-06-first-salary.md
    ├── 2025-02-09-deepseek-local-deploy.md
    ├── 2025-02-17-one-month-work-reflection.md
    ├── 2025-03-01-shallow-vs-deep-copy.md
    ├── 2025-03-16-probation-period.md
    ├── 2025-04-20-unemployed-new-beginning.md
    ├── 2025-05-23-job-hunt-one-month.md
    └── 2025-06-20-restful-apis.md
```

---

## 导航菜单

| 菜单   | 路径           |
|--------|----------------|
| Home   | `/`            |
| Posts  | `/posts/`      |
| Categories | `/categories/` |
| Tags   | `/tags/`       |
| Archives | `/archives/`   |
| About  | `/about/`      |
| Search | `/search/`     |

---

## 配置摘要

- **baseURL**: `https://jacvan.dev/`
- **title**: Jf | Blogs
- **评论仓库**: Alwaysdebugg/blog-comments
- **评论语言**: 中文
- **默认主题**: 跟随系统

---

## 本地开发

```bash
# 安装 Hugo
brew install hugo   # macOS

# 本地预览（含草稿）
hugo server -D

# 仅发布内容
hugo server

# 构建
hugo
```

访问: http://localhost:1313

---

## 版本信息

| 项目     | 版本      |
|----------|-----------|
| Hugo     | 0.146.0+  |
| PaperMod | 最新      |
| 发布日期 | 2025-03-01 |

---

## 如何发布文章

### 一、创建新文章

在 `content/posts/` 下新建 Markdown 文件，建议命名：`YYYY-MM-DD-文章标题-slug.md`。

```bash
# 示例
touch content/posts/2025-03-15-my-new-post.md
```

### 二、编写 Front Matter

每篇文章开头需包含 YAML 元数据，示例如下：

```yaml
---
title: "文章标题"
date: 2025-03-15
draft: true              # true=草稿，false=发布
description: "文章摘要，用于列表和 SEO"
tags:
  - 标签1
  - 标签2
categories:
  - 分类名
cover:
  image: "/images/cover.jpeg"   # 封面图路径
  alt: "封面描述"
  caption: ""
  hidden: false
---
```

| 字段 | 必填 | 说明 |
|------|------|------|
| title | ✅ | 文章标题 |
| date | ✅ | 发布日期 (YYYY-MM-DD) |
| draft | ✅ | `false` 表示发布，`true` 表示草稿 |
| description | 推荐 | 摘要，显示在列表页 |
| tags | 可选 | 标签列表 |
| categories | 可选 | 分类列表 |
| cover | 可选 | 封面图配置 |

### 三、撰写正文

在 Front Matter 下方的 `---` 之后用 **Markdown** 写正文，支持：

- 标题、列表、引用
- 代码块（自动高亮）
- 图片、链接
- 表格
- Emoji

### 四、本地预览

```bash
# 含草稿预览
hugo server -D

# 仅预览已发布文章
hugo server
```

浏览器打开 http://localhost:1313 检查效果。

### 五、发布到线上

1. **将草稿改为发布**：把 Front Matter 中的 `draft: true` 改为 `draft: false`。
2. **提交并推送**：
   ```bash
   git add content/posts/2025-03-15-my-new-post.md
   git commit -m "Post: 我的新文章"
   git push origin main
   ```
3. **自动部署**：推送到 `main` 后，GitHub Actions 会自动构建并部署到 GitHub Pages，约 1–2 分钟生效。

### 六、手动触发部署

如需在不改代码的情况下重新部署：

1. 打开仓库 → **Actions** → **Deploy Hugo to GitHub Pages**
2. 点击 **Run workflow** → **Run workflow**

### 七、常见问题

| 问题 | 处理方式 |
|------|----------|
| 文章未显示 | 检查 `draft` 是否为 `false`，文件名是否在 `content/posts/` 下 |
| 封面图不显示 | 确保图片在 `static/images/` 下，路径以 `/images/xxx` 开头 |
| 部署失败 | 查看 Actions 日志，确认 Hugo 版本与配置无误 |

---

*如有问题或建议，欢迎在 GitHub 提 Issue 或通过 Giscus 评论反馈。*
