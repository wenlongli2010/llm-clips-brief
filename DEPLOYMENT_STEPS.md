# GitHub Pages 部署步骤（详细版）

## 准备工作

### 1. 准备文件

在本地创建以下结构：

```
llm-clips-brief/
├── index.html
└── assets/
    └── wechat-qr.jpg
```

将 `微信图片_20260725011507_73_2.jpg` 重命名为 `wechat-qr.jpg` 并放入 `assets/` 文件夹。

---

## 方式一：通过 GitHub 网页端部署（推荐新手）

### 步骤 1: 创建仓库

1. 访问 https://github.com/new
2. Repository name: `llm-clips-brief`
3. Description: `LLM-Clips Founder Brief - 探索AI辅助数字芯片设计`
4. Public 公开
5. 不勾选 "Add a README file"
6. 点击 "Create repository"

### 步骤 2: 上传文件

1. 在新仓库页面点击 "uploading an existing file"
2. 将 `index.html` 拖拽到上传区域
3. 点击 "Commit changes"
4. 返回仓库首页
5. 点击 "Add file" > "Create new file"
6. 文件名输入: `assets/wechat-qr.jpg`（输入斜杠会自动创建文件夹）
7. 上传微信二维码图片
8. 点击 "Commit changes"

### 步骤 3: 启用 GitHub Pages

1. 点击仓库顶部 "Settings"
2. 左侧菜单找到 "Pages"
3. 在 "Branch" 下拉菜单选择 `main`
4. 目录选择 `/ (root)`
5. 点击 "Save"
6. 等待 1-3 分钟，页面顶部会显示：
   ```
   Your site is live at https://wenlongli2010.github.io/llm-clips-brief/
   ```

---

## 方式二：通过 Git 命令行部署（推荐熟练用户）

### 步骤 1: 初始化仓库

```bash
# 创建项目文件夹
mkdir llm-clips-brief
cd llm-clips-brief

# 初始化 Git
git init

# 复制 index.html 到此文件夹
# 创建 assets 文件夹并复制微信二维码

# 添加文件
git add .
git commit -m "Initial commit: LLM-Clips Founder Brief v1.0"
```

### 步骤 2: 关联远程仓库

```bash
# 在 GitHub 创建仓库后，关联远程地址
git remote add origin https://github.com/wenlongli2010/llm-clips-brief.git

# 推送到 GitHub
git branch -M main
git push -u origin main
```

### 步骤 3: 启用 GitHub Pages

同方式一的步骤 3。

---

## 验证部署

### 1. 访问页面

打开浏览器访问：
```
https://wenlongli2010.github.io/llm-clips-brief/
```

### 2. 检查清单

- [ ] 页面正常加载（无 404 错误）
- [ ] 标题显示 "LLM-Clips | Founder Brief"
- [ ] 深色模式自动跟随系统
- [ ] 移动端响应式正常（用手机或浏览器开发者工具测试）
- [ ] 微信二维码图片正常显示
- [ ] Email 链接 `bobwikely@gmail.com` 可点击
- [ ] 所有文字内容完整显示
- [ ] 工作流 SVG 图表正常渲染

---

## 生成 QR Code

### 方法 1: 在线生成（最简单）

1. 访问 https://www.qr-code-generator.com/
2. 选择 "URL" 类型
3. 输入: `https://wenlongli2010.github.io/llm-clips-brief/`
4. 点击 "Create QR Code"
5. 下载 PNG 格式（推荐 300x300 或更大）
6. 保存为 `llm-clips-brief-qr.png`

### 方法 2: 使用 Python

```bash
# 安装依赖
pip install qrcode[pil]

# 生成二维码
python3 << EOF
import qrcode

# 创建二维码
qr = qrcode.QRCode(
    version=1,
    error_correction=qrcode.constants.ERROR_CORRECT_L,
    box_size=10,
    border=4,
)
qr.add_data('https://wenlongli2010.github.io/llm-clips-brief/')
qr.make(fit=True)

# 生成图片
img = qr.make_image(fill_color="black", back_color="white")
img.save("llm-clips-brief-qr.png")
print("✅ QR code generated: llm-clips-brief-qr.png")
EOF
```

### 方法 3: 使用 Node.js

```bash
# 安装依赖
npm install -g qrcode

# 生成二维码（PNG）
qrcode -o llm-clips-brief-qr.png "https://wenlongli2010.github.io/llm-clips-brief/"

# 或生成 SVG（矢量图，可无限放大）
qrcode -t svg -o llm-clips-brief-qr.svg "https://wenlongli2010.github.io/llm-clips-brief/"
```

---

## 更新内容

如需修改页面内容：

1. 编辑本地 `index.html`
2. 推送到 GitHub：
   ```bash
   git add index.html
   git commit -m "Update content"
   git push
   ```
3. 等待 1-3 分钟自动重新部署

---

## 常见问题

### Q1: 页面显示 404

**解决方案**:
- 检查 GitHub Pages 是否已启用（Settings > Pages）
- 确认分支选择正确（main）
- 等待 3-5 分钟（首次部署需要时间）

### Q2: 图片不显示

**解决方案**:
- 检查图片路径：应为 `assets/wechat-qr.jpg`
- 检查图片是否已上传到仓库
- 清除浏览器缓存刷新页面

### Q3: 样式不生效

**解决方案**:
- 检查 `index.html` 是否完整
- 使用浏览器开发者工具（F12）查看 Console 错误
- 清除缓存或使用隐身模式访问

### Q4: 如何使用自定义域名

1. 在仓库根目录创建 `CNAME` 文件
2. 文件内容写入自定义域名（如 `brief.llm-clips.com`）
3. 在域名提供商处添加 DNS 记录：
   ```
   Type: CNAME
   Host: brief
   Value: wenlongli2010.github.io
   ```

---

## 技术支持

- GitHub Pages 官方文档: https://docs.github.com/pages
- 问题反馈: bobwikely@gmail.com

---

**部署状态**: ✅ 准备就绪  
**版本**: v1.0  
**最后更新**: 2026-07-25
