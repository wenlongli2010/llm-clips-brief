# LLM-Clips Founder Brief - Deployment Package

## 部署到 GitHub Pages

### 步骤 1: 创建新仓库或使用现有仓库

在 https://github.com/wenlongli2010 下创建名为 `llm-clips-brief` 的新仓库（或使用现有仓库）

### 步骤 2: 上传文件

将以下文件上传到仓库根目录：

```
index.html
assets/
  └── wechat-qr.jpg
```

### 步骤 3: 启用 GitHub Pages

1. 进入仓库 Settings
2. 左侧菜单选择 Pages
3. Source 选择 `main` 分支
4. 目录选择 `/ (root)`
5. 点击 Save

### 步骤 4: 等待部署完成

GitHub 会自动部署，通常需要 1-3 分钟

### 访问地址

部署完成后，访问地址为：

```
https://wenlongli2010.github.io/llm-clips-brief/
```

或如果使用用户页面仓库（仓库名为 wenlongli2010.github.io）：

```
https://wenlongli2010.github.io/
```

## QR Code 生成

部署完成后，使用以下任一方式生成二维码：

### 方法 1: 在线生成器
- https://www.qr-code-generator.com/
- 输入 URL: `https://wenlongli2010.github.io/llm-clips-brief/`
- 下载 PNG 格式

### 方法 2: 使用 Python
```bash
pip install qrcode[pil]
python -c "import qrcode; qrcode.make('https://wenlongli2010.github.io/llm-clips-brief/').save('founder-brief-qr.png')"
```

### 方法 3: 使用 CLI 工具
```bash
npm install -g qrcode
qr "https://wenlongli2010.github.io/llm-clips-brief/" > founder-brief-qr.svg
```

## 文件说明

- `index.html` - Founder Brief 主页面
- `assets/wechat-qr.jpg` - 微信二维码图片

## 注意事项

1. **图片路径**: 确保将微信二维码图片重命名为 `wechat-qr.jpg` 并放置在 `assets/` 文件夹
2. **仓库名**: 如果使用不同仓库名，需要相应调整访问 URL
3. **HTTPS**: GitHub Pages 自动启用 HTTPS
4. **缓存**: 如果更新后未生效，清除浏览器缓存或使用隐身模式访问

## 验证部署

部署完成后，访问 URL 验证：

✅ 页面正常加载
✅ 样式正常显示
✅ 深色模式切换正常
✅ 移动端响应式正常
✅ 微信二维码图片正常显示
✅ Email 链接可点击

## 更新内容

如需更新内容，直接推送新的 `index.html` 到仓库，GitHub Pages 会自动重新部署。

---

**Status**: Ready for Deployment  
**Version**: v1.0  
**Last Updated**: 2026-07-25
