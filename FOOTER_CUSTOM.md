# Footer 自定义说明

## 当前底部显示内容

博客底部默认显示：
- **Feed** - RSS 订阅链接（由 jekyll-feed 插件自动生成）
- **© 2026 powcai. Powered by Jekyll & Minimal Mistakes.** - 版权信息

## 自定义方法

### 方法 1：通过配置文件（推荐）

在 `_config.yml` 中已添加了 footer 配置：

```yaml
# Footer 配置
footer:
  links:
    - label: "Feed"
      icon: "fas fa-rss-square"
      url: "/feed.xml"

# 版权信息（如果需要自定义）
site_footer_text: "© 2026 powcai. Powered by Jekyll & Minimal Mistakes."
```

### 方法 2：创建自定义 Footer 文件

如果需要完全自定义 footer，可以创建 `_includes/footer-custom.html`：

```html
<footer class="page__footer">
  <div class="page__footer-copyright">
    <p>&copy; {{ site.time | date: '%Y' }} {{ site.name | default: site.title }}. 
    Powered by <a href="https://jekyllrb.com" rel="nofollow">Jekyll</a> &amp; 
    <a href="https://mademistakes.com/work/minimal-mistakes-jekyll-theme/" rel="nofollow">Minimal Mistakes</a>.</p>
  </div>
</footer>
```

然后在 `_config.yml` 中启用：

```yaml
footer:
  custom: true
```

### Feed 链接说明

- **Feed** 链接指向 `/feed.xml`
- 这是 RSS 订阅源，读者可以使用 RSS 阅读器订阅你的博客
- 由 `jekyll-feed` 插件自动生成
- 已添加到 `plugins` 列表中

### 版权信息自定义

可以修改 `site_footer_text` 来自定义版权信息，例如：

```yaml
site_footer_text: "© 2026 powcai. 长期写作，持续成长。"
```

或者：

```yaml
site_footer_text: "© 2026 powcai. All rights reserved."
```

## 注意事项

1. **Feed 链接**：需要 `jekyll-feed` 插件支持（已添加）
2. **版权年份**：可以使用 `{{ site.time | date: '%Y' }}` 自动获取当前年份
3. **使用 remote_theme**：某些深度自定义可能需要 fork 主题或使用本地主题

## 当前配置状态

✅ 已启用 `jekyll-feed` 插件
✅ 已添加 footer 配置
✅ Feed 链接将自动显示在底部

如果需要修改版权文字，直接编辑 `_config.yml` 中的 `site_footer_text` 即可。
