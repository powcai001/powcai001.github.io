# 分享按钮自定义说明

## 已完成的自定义

### 1. 自定义分享按钮

已创建 `_includes/page__share.html` 文件，只显示：
- ✅ **X (Twitter)** - 分享到 X/Twitter
- ✅ **微信** - 分享到微信（带二维码）

### 2. 禁用相关文章推荐

在 `_config.yml` 中已设置：
```yaml
related: false  # 禁用 "You May Also Enjoy" 部分
```

## 功能说明

### X (Twitter) 分享
- 点击后打开 Twitter 分享窗口
- 自动填充文章标题和链接

### 微信分享
- 点击后显示二维码弹窗
- 使用微信扫描二维码即可分享
- 二维码包含当前文章链接

## 如果主题使用不同的 include 文件名

Minimal Mistakes 主题可能使用以下文件名之一：
- `page__share.html` ✅ (已创建)
- `social-share.html`
- `share-buttons.html`

如果自定义文件不生效，可能需要：
1. 检查主题使用的实际文件名
2. 或者创建多个可能的文件名

## 测试方法

1. 提交更改到 GitHub
2. 等待 GitHub Pages 构建完成
3. 访问任意文章页面
4. 检查分享按钮是否只显示 X 和微信
5. 检查是否还有 "You May Also Enjoy" 部分

## 如果需要重新启用相关文章

如果以后想重新启用 "You May Also Enjoy" 部分，只需在 `_config.yml` 中修改：

```yaml
related: true  # 启用相关文章推荐
```

## 注意事项

- 使用 `remote_theme` 时，自定义的 `_includes` 文件会覆盖主题默认文件
- 微信分享使用在线二维码生成服务（api.qrserver.com）
- 如果需要更稳定的二维码服务，可以替换为其他服务
