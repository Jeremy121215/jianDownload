网址：https://jeremy121215.github.io/jianDownload/

# 下载网站导航

一个基于纯前端技术构建的下载网站导航系统，支持多分类管理、搜索功能和便捷的内容维护。

## 功能特点

- 📁 **多分类管理**：支持音乐资源、图书资源等多种资源类型
- 🔍 **强大搜索功能**：支持全局搜索和分类内搜索
- 📱 **响应式设计**：适配不同屏幕尺寸
- 🎨 **现代化UI**：简洁美观的用户界面
- 📝 **便捷维护**：通过JSON文件即可轻松添加和修改内容
- 🔗 **直接下载**：点击即可下载资源，无需跳转
- 📂 **子分类支持**：每个分类可包含多个子分类
- 🎯 **分类筛选**：支持按子分类筛选资源

## 项目结构

```
download/
├── index.html          # 主页面 - 分类导航
├── download.html       # 下载页面
├── css/
│   ├── style.css      # 通用样式
│   ├── index.css      # 首页样式
│   └── download.css   # 下载页面样式
├── js/
│   ├── main.js        # 通用功能
│   ├── index.js       # 首页逻辑
│   └── download.js    # 下载页面逻辑
├── data/
│   ├── navigation.json # 导航分类数据
│   ├── music.json      # 音乐分类数据
│   └── books.json      # 图书分类数据
├── downloads/
│   ├── music/         # 音乐下载文件目录
│   └── books/         # 图书下载文件目录
└── README.md          # 项目说明文档
```

## 快速开始

### 本地运行

1. **克隆或下载项目**
   将项目文件下载到本地目录

2. **启动本地服务器**
   - 使用PowerShell（Windows）：
     ```powershell
     $listener = New-Object System.Net.HttpListener; $listener.Prefixes.Add('http://localhost:8080/'); $listener.Start(); Write-Host 'Phigros Web 服务器已启动！'; Write-Host '访问地址：http://localhost:8080'; Write-Host '服务器正在运行中...'; while ($true) { try { $context = $listener.GetContext(); $request = $context.Request; $response = $context.Response; $localPath = $request.Url.LocalPath; if ($localPath -eq '/') { $localPath = '/index.html'; } $filePath = [System.IO.Path]::Combine((Get-Location).Path, $localPath.Substring(1)); if ([System.IO.File]::Exists($filePath)) { $contentType = 'text/plain'; $ext = [System.IO.Path]::GetExtension($filePath).ToLower(); switch ($ext) { '.html' { $contentType = 'text/html' } '.css' { $contentType = 'text/css' } '.js' { $contentType = 'application/javascript' } '.json' { $contentType = 'application/json' } '.mp3' { $contentType = 'audio/mpeg' } '.wav' { $contentType = 'audio/wav' } '.ogg' { $contentType = 'audio/ogg' } '.m4a' { $contentType = 'audio/mp4' } '.jpg' { $contentType = 'image/jpeg' } '.jpeg' { $contentType = 'image/jpeg' } '.png' { $contentType = 'image/png' } } $response.ContentType = $contentType; $content = [System.IO.File]::ReadAllBytes($filePath); $response.ContentLength64 = $content.Length; $response.OutputStream.Write($content, 0, $content.Length); } else { $response.StatusCode = 404; } $response.Close(); } catch { Write-Host 'Error:', $_; } }
     ```

3. **访问网站**
   在浏览器中输入：http://localhost:8083

### 部署到GitHub Pages

1. **创建GitHub仓库**
   创建一个新的GitHub仓库

2. **上传项目文件**
   将项目文件上传到GitHub仓库

3. **启用GitHub Pages**
   - 进入仓库设置
   - 选择"Pages"选项
   - 选择分支（通常为main或master）
   - 选择根目录
   - 点击"Save"保存

4. **访问网站**
   等待部署完成后，通过GitHub Pages提供的URL访问网站
   （格式：https://<username>.github.io/<repository-name>/）

### 浏览分类

1. **首页分类**
   - 首页展示所有可用的资源分类
   - 每个分类卡片显示分类名称、图标和描述
   - 点击"进入"按钮或卡片任意位置进入对应分类的下载页面

2. **下载页面**
   - 页面顶部显示当前分类名称
   - 提供"返回首页"按钮
   - 显示当前分类的所有子分类
   - 显示当前分类的所有资源文件

### 搜索资源

1. **全局搜索**
   - 在首页顶部的搜索框中输入关键词
   - 点击"搜索"按钮或按Enter键
   - 系统会筛选出名称或描述包含关键词的分类

2. **分类内搜索**
   - 在下载页面顶部的搜索框中输入关键词
   - 点击"搜索"按钮或按Enter键
   - 系统会筛选出当前分类中名称或描述包含关键词的资源

### 筛选资源

1. **按子分类筛选**
   - 在下载页面中，点击对应子分类标签
   - 系统会显示该子分类下的所有资源
   - 点击"全部"标签可显示所有资源

### 下载文件

1. **直接下载**
   - 在下载页面中，找到需要下载的资源
   - 点击资源卡片上的"下载"按钮
   - 浏览器会自动开始下载文件

2. **右键下载**
   - 右键点击"下载"按钮
   - 选择"另存为"或类似选项
   - 选择保存位置后开始下载

## 如何维护

### 修改分类

1. **修改导航分类**
   - 编辑 `data/navigation.json` 文件
   - 每个分类包含以下字段：
     ```json
     {
         "id": "分类ID",
         "name": "分类名称",
         "icon": "Font Awesome图标类名",
         "description": "分类描述"
     }
     ```
   - 保存文件后，刷新网站即可看到修改效果

2. **修改分类数据**
   - 编辑对应分类的JSON文件（如 `data/music.json`）
   - 可以修改分类名称、描述、子分类和资源文件
   - 保存文件后，刷新网站即可看到修改效果

### 添加资源

1. **准备资源文件**
   - 将资源文件上传到对应分类的下载目录中
   - 例如：音乐文件上传到 `downloads/music/` 目录
   - 图书文件上传到 `downloads/books/` 目录

2. **添加资源信息**
   - 编辑对应分类的JSON文件（如 `data/music.json`）
   - 在 `files` 数组中添加新的资源信息：
     ```json
     {
         "id": "资源ID",
         "name": "资源名称",
         "icon": "Font Awesome图标类名",
         "description": "资源描述",
         "subcategory": "子分类ID",
         "link": "资源文件路径"
     }
     ```
   - 资源ID：唯一标识，建议使用英文字母、数字和下划线
   - 资源名称：显示给用户的资源名称
   - 图标：使用Font Awesome图标，如 `fas fa-music`、`fas fa-book`、`fas fa-file-pdf` 等
   - 描述：资源的简短描述
   - 子分类：资源所属的子分类ID
   - 链接：资源文件的相对路径，如 `downloads/music/歌曲名称.mp3`

3. **保存修改**
   - 保存JSON文件
   - 刷新网站即可看到新添加的资源

### 添加新分类

1. **创建分类目录**
   - 在 `downloads/` 目录下创建新的分类目录
   - 例如：创建软件分类目录 `downloads/software/`

2. **添加导航分类**
   - 编辑 `data/navigation.json` 文件
   - 在数组中添加新的分类信息：
     ```json
     {
         "id": "software",
         "name": "软件资源",
         "icon": "fas fa-download",
         "description": "各类软件下载资源"
     }
     ```

3. **创建分类数据文件**
   - 在 `data/` 目录下创建新的分类JSON文件
   - 文件名与分类ID相同，如 `data/software.json`
   - 文件内容格式：
     ```json
     {
         "category": "分类ID",
         "name": "分类名称",
         "description": "分类描述",
         "subcategories": [
             {
                 "id": "子分类ID",
                 "name": "子分类名称"
             }
         ],
         "files": [
             // 资源文件列表
         ]
     }
     ```

4. **添加资源**
   - 参考「添加资源」部分，添加该分类的资源文件

### 修改样式

1. **修改通用样式**
   - 编辑 `css/style.css` 文件
   - 包含全局样式、布局和响应式设计

2. **修改首页样式**
   - 编辑 `css/index.css` 文件
   - 包含首页特有的样式，如分类卡片样式

3. **修改下载页面样式**
   - 编辑 `css/download.css` 文件
   - 包含下载页面特有的样式，如资源卡片样式

## 技术栈

- **前端技术**：HTML5、CSS3、JavaScript（ES6+）
- **样式框架**：Font Awesome（图标库）
- **数据存储**：JSON文件
- **部署方式**：静态网站部署

## 浏览器支持

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## 许可证

本项目采用 MIT 许可证，详见 LICENSE 文件。

## 贡献

欢迎提交 Issue 和 Pull Request！

## 更新日志

### v1.0.0 (2026-01-18)
- 初始化项目
- 添加音乐资源分类
- 添加图书资源分类
- 实现基本的搜索和筛选功能

## 联系方式

如有问题或建议，欢迎通过以下方式联系：

- 项目地址：[https://github.com/Jeremy121215/jianDownload/]
- 邮箱：[xhwm121215@qq.com 或 ]

---

**© 2026 下载网站导航**

本项目仅供学习和参考使用，资源内容请确保符合相关法律法规。
