# Jekyll + Minimal Mistakes 使用指南

## 📚 目录
1. [什么是 Jekyll](#什么是-jekyll)
2. [什么是 Minimal Mistakes](#什么是-minimal-mistakes)
3. [配置文件详解](#配置文件详解)
4. [文件结构说明](#文件结构说明)
5. [如何创建和发布文章](#如何创建和发布文章)
6. [常用功能](#常用功能)
7. [自定义和扩展](#自定义和扩展)

---

## 什么是 Jekyll

**Jekyll** 是一个静态网站生成器，可以将 Markdown 文件转换为静态 HTML 网站。

### 核心特点：
- ✅ **简单易用**：使用 Markdown 写文章，无需数据库
- ✅ **GitHub Pages 原生支持**：推送到 GitHub 自动构建和部署
- ✅ **快速**：生成静态 HTML，加载速度快
- ✅ **安全**：没有动态服务器，减少安全风险
- ✅ **版本控制**：所有内容都在 Git 仓库中

### 工作原理：
```
Markdown 文件 + 配置文件 → Jekyll 处理 → 静态 HTML 网站
```

---

## 什么是 Minimal Mistakes

**Minimal Mistakes** 是一个功能丰富、高度可定制的 Jekyll 主题。

### 主要特性：
- 🎨 **多种皮肤**：内置多种配色方案
- 📱 **响应式设计**：完美适配手机、平板、电脑
- 🔍 **SEO 优化**：内置搜索引擎优化
- 📊 **多种布局**：支持文章列表、单页、归档等多种布局
- 🎯 **易于定制**：通过配置文件即可自定义

### 为什么选择 Minimal Mistakes：
1. **文档完善**：官方文档详细
2. **社区活跃**：使用广泛，问题容易解决
3. **功能丰富**：满足博客、作品集、文档站等多种需求
4. **持续更新**：维护活跃

---

## 配置文件详解

### `_config.yml` 文件说明

这是 Jekyll 的核心配置文件，控制整个网站的行为。

#### 1. 基本信息配置

```yaml
title: "powcai"                    # 网站标题，显示在浏览器标签页
description: "长期写作｜技术与思考"  # 网站描述，用于 SEO
url: "https://powcai001.github.io" # 网站的完整 URL
baseurl: ""                        # 子路径，如果网站不在根目录则填写
```

**说明**：
- `url` 必须是完整的 URL（包含 `https://`）
- `baseurl` 如果网站部署在根目录，保持为空字符串 `""`

#### 2. 主题配置

```yaml
remote_theme: "mmistakes/minimal-mistakes"  # 使用远程主题（GitHub Pages 推荐方式）
plugins:
  - jekyll-include-cache                    # 缓存插件，提升性能

minimal_mistakes_skin: "default"            # 主题皮肤：default, air, dark, mint, neon 等
```

**主题皮肤选项**：
- `default` - 默认白色主题
- `air` - 简洁的浅色主题
- `dark` - 深色主题
- `mint` - 薄荷绿主题
- `neon` - 霓虹主题
- `plum` - 紫色主题
- `sunrise` - 日出主题

**如何更换皮肤**：
只需修改 `minimal_mistakes_skin` 的值即可。

#### 3. Markdown 和链接配置

```yaml
markdown: kramdown                    # Markdown 解析引擎（推荐 kramdown）
permalink: /:categories/:title/      # 文章 URL 格式
paginate: 8                           # 每页显示的文章数量
paginate_path: /page:num/            # 分页 URL 格式
```

**permalink 格式说明**：
- `/:categories/:title/` - 分类/标题/
- `/:year/:month/:day/:title/` - 年/月/日/标题/
- `/:title/` - 仅标题
- `/blog/:year/:month/:day/:title/` - 带前缀的路径

**示例**：
- 文章标题：`我的第一篇文章`
- 分类：`技术`
- 最终 URL：`https://powcai001.github.io/技术/我的第一篇文章/`

#### 4. 作者信息配置

```yaml
author:
  name: "powcai"                      # 作者名称
  avatar: "/assets/images/avatar.png" # 头像路径（放在 assets/images/ 目录）
  bio: "长期写作｜技术与思考"          # 作者简介
  links:                              # 社交链接
    - label: "GitHub"
      icon: "fab fa-github"           # Font Awesome 图标
      url: "https://github.com/powcai001"
```

**支持的社交图标**（Font Awesome）：
- `fab fa-github` - GitHub
- `fab fa-twitter` - Twitter
- `fab fa-linkedin` - LinkedIn
- `fab fa-weibo` - 微博
- `fas fa-envelope` - 邮箱
- `fab fa-zhihu` - 知乎

**添加更多链接**：
```yaml
links:
  - label: "GitHub"
    icon: "fab fa-github"
    url: "https://github.com/powcai001"
  - label: "邮箱"
    icon: "fas fa-envelope"
    url: "mailto:your@email.com"
  - label: "博客"
    icon: "fas fa-blog"
    url: "https://yourblog.com"
```

#### 5. 导航菜单配置

```yaml
navigation:
  main:
    - title: "主页"
      url: /
    - title: "博客"
      url: /blog/
    - title: "关于"
      url: /about/
```

**添加更多菜单项**：
```yaml
navigation:
  main:
    - title: "主页"
      url: /
    - title: "博客"
      url: /blog/
    - title: "归档"
      url: /year-archive/
    - title: "标签"
      url: /tags/
    - title: "关于"
      url: /about/
```

#### 6. 默认配置

```yaml
defaults:
  - scope:
      path: ""              # 路径范围（空表示所有路径）
      type: posts           # 文件类型（posts 表示文章）
    values:
      layout: single        # 布局类型
      author_profile: true  # 显示作者信息
      read_time: true       # 显示阅读时间
      comments: false      # 关闭评论（GitHub Pages 默认不支持）
      share: true           # 显示分享按钮
      related: true        # 显示相关文章
```

**布局类型说明**：
- `single` - 单栏布局，适合文章
- `splash` - 全屏布局，适合首页
- `archive` - 归档布局
- `home` - 首页布局，显示文章列表

---

## 文件结构说明

```
powcai001.github.io/
├── _config.yml          # Jekyll 配置文件（核心）
├── index.md             # 首页文件
├── about.md             # 关于页面
├── blog.md              # 博客列表页
├── _posts/              # 文章目录（重要！）
│   ├── 2026-01-26-hello.md
│   └── TEMPLATE.md
├── assets/              # 静态资源目录
│   └── images/         # 图片目录
│       └── avatar.png   # 头像（需要自己添加）
└── README.md            # 项目说明
```

### 关键目录说明：

#### `_posts/` 目录
- **作用**：存放所有博客文章
- **命名规则**：`YYYY-MM-DD-文章标题.md`
- **示例**：`2026-01-27-我的技术文章.md`
- **注意**：文件名中的日期必须正确，Jekyll 会根据日期排序

#### `assets/images/` 目录
- **作用**：存放图片资源
- **使用**：在文章中使用 `/assets/images/图片名.png` 引用

---

## 如何创建和发布文章

### 步骤 1：创建文章文件

在 `_posts/` 目录下创建新文件，命名格式：`YYYY-MM-DD-文章标题.md`

**示例**：
```
_posts/2026-01-27-学习Python的心得.md
```

### 步骤 2：编写文章 Front Matter

每篇文章开头必须有 Front Matter（YAML 前置元数据）：

```yaml
---
title: "文章标题"
date: 2026-01-27
tags: [Python, 学习, 编程]
categories: [技术]
---
```

**Front Matter 字段说明**：
- `title` - 文章标题（必需）
- `date` - 发布日期（必需，格式：YYYY-MM-DD）
- `tags` - 标签（可选，数组格式）
- `categories` - 分类（可选，可以是字符串或数组）
- `layout` - 布局（可选，默认使用配置中的设置）

### 步骤 3：编写文章内容

使用 Markdown 语法编写内容：

```markdown
## 标题

这是正文内容。

### 代码示例

```python
def hello():
    print("Hello, World!")
```

### 列表

- 项目 1
- 项目 2

### 链接和图片

[链接文本](https://example.com)
![图片描述](/assets/images/example.png)
```

### 步骤 4：提交到 GitHub

```bash
git add _posts/2026-01-27-学习Python的心得.md
git commit -m "Add new post: 学习Python的心得"
git push origin main
```

**GitHub Pages 会自动构建**，几分钟后文章就会出现在网站上。

---

## 常用功能

### 1. 文章分类和标签

**分类（Categories）**：
```yaml
categories: [技术]              # 单个分类
categories: [技术, Python]     # 多个分类
```

**标签（Tags）**：
```yaml
tags: [Python, 学习, 编程]     # 多个标签
```

### 2. 插入图片

1. 将图片放到 `assets/images/` 目录
2. 在文章中使用：
```markdown
![图片描述](/assets/images/图片名.png)
```

### 3. 代码高亮

使用三个反引号包裹代码，并指定语言：

````markdown
```python
def hello():
    print("Hello, World!")
```
````

支持的语言：`python`, `javascript`, `java`, `go`, `html`, `css`, `bash` 等。

### 4. 引用和提示

```markdown
> 这是一个引用块

**提示**：这是重要提示
```

### 5. 表格

```markdown
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 数据1 | 数据2 | 数据3 |
```

---

## 自定义和扩展

### 1. 更换主题皮肤

修改 `_config.yml`：
```yaml
minimal_mistakes_skin: "dark"  # 改为 dark
```

### 2. 添加自定义 CSS

创建 `assets/css/main.scss`：
```scss
---
---

// 自定义样式
.my-custom-class {
  color: blue;
}
```

### 3. 添加自定义页面

创建新文件，例如 `projects.md`：
```yaml
---
layout: single
title: "项目"
permalink: /projects/
---

# 我的项目

项目内容...
```

### 4. 使用插件

在 `_config.yml` 中添加：
```yaml
plugins:
  - jekyll-include-cache
  - jekyll-feed          # RSS 订阅
  - jekyll-sitemap      # 网站地图
```

**注意**：GitHub Pages 只支持[官方插件列表](https://pages.github.com/versions/)中的插件。

---

## 最佳实践

### ✅ 推荐做法：

1. **文章命名**：使用有意义的文件名，避免特殊字符
2. **定期更新**：保持博客活跃，定期发布文章
3. **图片优化**：压缩图片大小，提升加载速度
4. **SEO 优化**：为每篇文章添加描述和关键词
5. **版本控制**：每次修改都提交到 Git

### ❌ 避免：

1. 不要在文件名中使用中文（虽然支持，但可能导致 URL 编码问题）
2. 不要上传过大的文件到仓库
3. 不要在 Front Matter 中使用特殊字符
4. 不要忘记提交 `_config.yml` 的更改

---

## 常见问题

### Q: 文章发布后看不到？
A: 检查文件名格式是否正确（YYYY-MM-DD-标题.md），等待几分钟让 GitHub Pages 构建完成。

### Q: 如何修改网站标题？
A: 修改 `_config.yml` 中的 `title` 字段。

### Q: 如何添加评论功能？
A: GitHub Pages 不支持动态评论，可以使用第三方服务如 Giscus（基于 GitHub Discussions）。

### Q: 如何备份博客？
A: 所有内容都在 Git 仓库中，推送到 GitHub 就是备份。

### Q: 本地预览如何操作？
A: 安装 Jekyll，运行 `jekyll serve`，访问 `http://localhost:4000`。

---

## 参考资源

- [Jekyll 官方文档](https://jekyllrb.com/)
- [Minimal Mistakes 主题文档](https://mmistakes.github.io/minimal-mistakes/)
- [GitHub Pages 文档](https://docs.github.com/pages)
- [Markdown 语法指南](https://www.markdownguide.org/)

---

**提示**：遇到问题可以查看 GitHub Pages 的构建日志，在仓库的 Settings → Pages → Build and deployment 中查看。
