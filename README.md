# 此项目仅限个人使用，禁止用做商业行为
---
















## 🕒 最后更新时间

**UTC**: `2025-12-22 03:05:49`  
**北京时间**: `2025-12-22 11:05:49`  

> ⚡ 此时间戳由 GitHub Actions 自动更新

<<<<<<< HEAD
=======
<!-- 社交链接 -->
<a href="https://github.com/deerwan" target="_blank">GitHub</a>
<a href="mailto:mrdeer7@qq.com">邮箱</a>
```

### 2. API服务配置

在 `assets/js/modules/config.js` 中配置各种API服务：

```javascript
export const CONFIG = {
    // 背景图片API
    BING_WALLPAPER_URL: 'https://bing.img.run/rand.php',
    BING_FALLBACK_URL: 'https://api.dujin.org/bing/1920.php',
    
    // 一言API
    HITOKOTO_API: 'https://v1.hitokoto.cn/?c=a&c=b&c=c&c=d&c=h&c=i&c=k',
    HITOKOTO_BACKUP_API: 'https://api.uomg.com/api/rand.qinghua?format=json',
    
    // 友链推送API
    FRIEND_LINK_API: 'https://home-push-friend-link.952780.xyz/',
    
    // 性能配置
    API_TIMEOUT: 3000,
    WALLPAPER_TIMEOUT: 5000
};
```

### 3. 留言板配置（Giscus）

1. 访问 [Giscus官网](https://giscus.app/zh-CN)
2. 根据向导配置你的GitHub仓库
3. 在 `index.html` 中更新Giscus配置：

```html
<script src="https://giscus.app/client.js"
    data-repo="你的用户名/仓库名"
    data-repo-id="仓库ID"
    data-category="Announcements"
    data-category-id="分类ID"
    data-mapping="pathname"
    data-theme="dark_dimmed"
    data-lang="zh-CN"
    crossorigin="anonymous"
    async>
</script>
```

### 4. 音乐播放器配置

在 `index.html` 底部配置网易云音乐播放器：

```html
<meting-js
    server="netease"          <!-- 音乐平台：netease/qq/xiami/kugou -->
    type="playlist"           <!-- 类型：song/playlist/album/artist -->
    id="你的歌单ID"            <!-- 对应的ID -->
    fixed="true"              <!-- 固定模式 -->
    autoplay="true"           <!-- 自动播放 -->
    order="random"            <!-- 播放顺序：list/random -->
    theme="#4a89dc"           <!-- 主题色 -->
    loop="all"                <!-- 循环模式：all/one/none -->
    volume="0.7">             <!-- 默认音量 -->
</meting-js>
```

### 5. 友链推送配置（Cloudflare Worker）

1. **创建Cloudflare Worker**：
   - 登录Cloudflare仪表盘
   - 创建新的Worker
   - 复制 `push_friend_link.js` 内容到Worker

2. **设置环境变量**：
   ```
   TG_BOT_TOKEN=你的Telegram机器人Token
   TG_CHAT_ID=你的Telegram聊天ID
   FEISHU_WEBHOOK=你的飞书Webhook地址
   ```

3. **获取Telegram机器人**：
   - 与 @BotFather 对话创建机器人
   - 获取Bot Token
   - 获取Chat ID（可通过 @userinfobot）

4. **配置飞书机器人**：
   - 在飞书群中添加自定义机器人
   - 复制Webhook地址

### 6. PWA配置

编辑 `manifest.json` 配置PWA应用信息：

```json
{
  "name": "你的网站名称",
  "short_name": "简称",
  "description": "网站描述",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#121212",
  "theme_color": "#121212",
  "icons": [
    {
      "src": "assets/img/logo.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}
```

### 7. 导航链接管理

在 `index.html` 的导航区域添加或修改链接：

```html
<div class="nav-category">
    <h3><i class="fas fa-code"></i> 开发工具</h3>
    <div class="nav-links">
        <a class="nav-link-item" href="链接地址" target="_blank">
            <img src="图标地址" alt="名称" width="32" height="32" class="nav-icon">
            <div>
                <div class="nav-name">网站名称</div>
                <div class="nav-desc">网站描述</div>
            </div>
        </a>
    </div>
</div>
```

### 8. 部署配置

**web.config（IIS部署）**：
- 已配置HTTPS重定向、缓存策略、安全头
- 支持WebP图片、字体文件等MIME类型

**CNAME（自定义域名）**：
```
你的域名.com
```

**sitemap.xml（SEO优化）**：
更新网站地图中的URL和更新频率

---

## 🎨 自定义样式

### 主题色彩
在 `assets/css/style.css` 中修改CSS变量：

```css
:root {
    --primary-color: #4a89dc;
    --background-color: #121212;
    --text-color: #ffffff;
    --card-background: rgba(255, 255, 255, 0.1);
}
```

### 字体配置
项目使用阿里妈妈刀隶体，可在CSS中替换：

```css
@font-face {
    font-family: 'CustomFont';
    src: url('../fonts/YourFont.woff2') format('woff2');
}
```

---

## 🔧 开发说明

### 技术栈
- **前端**：HTML5 + CSS3 + ES6+ JavaScript
- **架构**：模块化设计，支持ES6 Modules
- **兼容性**：现代浏览器 + IE11降级支持
- **工具**：PWA、Service Worker、Web Components

### 模块说明
- `app.js`：现代版主应用，使用ES6模块
- `main.js`：兼容版本，支持旧浏览器
- `modules/`：功能模块化组件
  - `config.js`：配置管理
  - `api.js`：API接口处理
  - `background.js`：背景图片管理
  - `ui.js`：用户界面交互
  - `analytics.js`：数据分析
  - `error-handler.js`：错误处理

### 性能优化
- 图片懒加载和预加载
- CSS/JS异步加载
- 资源缓存策略
- 防抖函数优化
- Service Worker缓存

---

## 🐛 常见问题

### Q: 一言API无法加载？
A: 检查网络连接，或在config.js中更换备用API

### Q: 音乐播放器不工作？
A: 确保网易云歌单是公开的，检查歌单ID是否正确

### Q: 友链推送失败？
A: 检查Cloudflare Worker环境变量配置，确认API地址正确

### Q: 图片无法显示？
A: 检查图片路径，确保图片文件存在且可访问

### Q: 移动端显示异常？
A: 清除浏览器缓存，检查CSS媒体查询配置

---

## 📈 版本历史

- **v2.0.0**：模块化重构，添加ES6支持
- **v1.5.0**：添加音效系统和性能监控
- **v1.0.0**：初始版本发布

---

## 📄 开源协议

本项目基于 [Apache-2.0](LICENSE) 协议开源

---

## 🤝 贡献指南

欢迎提交 Pull Request 和 Issue！

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/新功能`
3. 提交更改：`git commit -am '添加新功能'`
4. 推送分支：`git push origin feature/新功能`
5. 提交 Pull Request

---

## 💬 联系方式

- **作者**：Deer
- **邮箱**：mrdeer7@qq.com
- **GitHub**：[@deerwan](https://github.com/deerwan)
- **博客**：[deerwan.github.io](https://deerwan.github.io)
## 🕒 最后更新时间

**UTC**: `2026-01-16 03:27:03`  
**北京时间**: `2026-01-16 11:27:03`  

> ⚡ 此时间戳由 GitHub Actions 自动更新

>>>>>>> f9cb1c959fd19f421f85a007a66d8a500c8b9d37
