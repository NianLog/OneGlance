# HTML基础知识

<span class="important-note">本教程系统讲解HTML基础知识，包括HTML文档结构、常用标签、HTML5语义化标签、表单和新特性等内容。</span>

## 一、HTML基础概念

### 1.1 什么是HTML？

HTML（HyperText Markup Language，超文本标记语言）是构建网页的基础语言。它不是编程语言，而是一种标记语言，用于定义网页的结构和内容。

### 1.2 HTML的版本发展

- **HTML 4.01**：1999年发布，经典的Web标准
- **XHTML 1.0**：基于XML的严格版本
- **HTML5**：2014年正式发布，引入了丰富的语义化标签和API

<span class="tip-box">HTML5是目前主流版本，几乎所有现代浏览器都支持。</span>

### 1.3 HTML的基本特点

- **简单易学**：标签语法清晰，易于理解
- **跨平台**：可在各种设备和浏览器上运行
- **可扩展**：配合CSS和JavaScript实现丰富的功能
- **免费开源**：无需授权，完全免费

## 二、HTML文档结构

### 2.1 基本文档结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>网页标题</title>
</head>
<body>
    <!-- 网页内容 -->
</body>
</html>
```

### 2.2 DOCTYPE声明

`<!DOCTYPE html>`告诉浏览器使用HTML5标准渲染页面。这个声明很重要，不同的DOCTYPE会影响浏览器的渲染模式。

<span class="warning-box">注意：DOCTYPE声明必须放在HTML文档的第一行，否则可能导致浏览器进入怪异模式。</span>

### 2.3 head标签详解

**head**标签包含网页的元信息，不会直接显示在页面上：

- **meta标签**：提供页面的元数据
  - `charset`：字符编码，推荐使用UTF-8
  - `viewport`：响应式设计必备
  - `description`：页面描述，SEO优化
- **title标签**：页面标题，显示在浏览器标签页上
- **link标签**：引入外部资源（CSS文件、图标等）

## 三、HTML标签详解

### 3.1 文本标签

#### 标题标签

```html
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
```

**注意事项**：
- 页面中h1标签通常只用一次
- 按照层级正确使用标题标签
- 标题标签对SEO很重要

<span class="tip-box">SEO技巧：h1标签应该包含页面的核心关键词，并且只出现一次。</span>

#### 段落和文本格式

```html
<p>段落文本</p>
<br> <!-- 换行 -->
<hr> <!-- 水平线 -->
<strong>粗体强调</strong>
<em>斜体强调</em>
<mark>标记文本</mark>
<del>删除线</del>
<ins>下划线</ins>
<sub>下标</sub>
<sup>上标</sup>
```

### 3.2 列表标签

#### 无序列表

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
</ul>
```

#### 有序列表

```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
    <li>第三项</li>
</ol>
```

#### 定义列表

```html
<dl>
    <dt>HTML</dt>
    <dd>超文本标记语言</dd>
    <dt>CSS</dt>
    <dd>层叠样式表</dd>
</dl>
```

### 3.3 链接和图片

#### 超链接

```html
<!-- 外部链接 -->
<a href="https://www.example.com" target="_blank">打开新窗口</a>

<!-- 内部链接 -->
<a href="about.html">关于页面</a>

<!-- 锚点链接 -->
<a href="#section1">跳转到第一节</a>

<!-- 邮件链接 -->
<a href="mailto:example@email.com">发送邮件</a>
```

**target属性值**：
- `_self`：当前窗口（默认）
- `_blank`：新窗口
- `_parent`：父框架
- `_top`：顶层框架

<span class="warning-box">注意：使用target="_blank"时，应添加rel="noopener noreferrer"以防止安全漏洞。</span>

#### 图片

```html
<img src="image.jpg" alt="图片描述" width="300" height="200">
```

**重要属性**：
- `src`：图片路径（必需）
- `alt`：替代文本（必需，用于SEO和无障碍访问）
- `width`/`height`：宽度和高度

<span class="tip-box">最佳实践：始终为图片添加alt属性，这对SEO和无障碍访问都很重要。</span>

### 3.4 表格标签

```html
<table border="1">
    <caption>表格标题</caption>
    <thead>
        <tr>
            <th>表头1</th>
            <th>表头2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>单元格1</td>
            <td>单元格2</td>
        </tr>
    </tbody>
</table>
```

## 四、HTML5语义化标签

### 4.1 语义化标签的重要性

语义化标签是描述内容含义的标签，而不是描述其外观。使用语义化标签的好处：

- **可访问性**：使屏幕阅读器能够理解内容
- **SEO优化**：有助于搜索引擎理解页面结构
- **代码维护**：使代码更易于理解和维护

<span class="important-note">语义化是现代Web开发的核心原则之一，应始终优先使用语义化标签。</span>

### 4.2 常用语义化标签

| 标签 | 用途 |
|------|------|
| `<header>` | 页面或区块头部 |
| `<nav>` | 导航菜单 |
| `<main>` | 页面核心内容 |
| `<article>` | 独立内容块 |
| `<section>` | 内容分组 |
| `<aside>` | 侧边栏或补充信息 |
| `<footer>` | 底部信息 |

### 4.3 语义化布局示例

```html
<header>
    <h1>网站标题</h1>
    <nav>
        <ul>
            <li><a href="#">首页</a></li>
            <li><a href="#">关于</a></li>
        </ul>
    </nav>
</header>
<main>
    <article>
        <h2>文章标题</h2>
        <p>文章内容...</p>
    </article>
    <aside>
        <h3>侧边栏</h3>
        <p>补充信息</p>
    </aside>
</main>
<footer>
    <p>版权信息</p>
</footer>
```

## 五、HTML表单

### 5.1 表单的基本结构

```html
<form action="submit.php" method="post">
    <!-- 表单控件 -->
</form>
```

**action属性**：指定表单数据提交的URL

**method属性**：
- `get`：数据附加在URL后面（适合非敏感数据）
- `post`：数据放在HTTP请求主体中（适合敏感数据）

<span class="tip-box">安全提示：涉及敏感信息（如密码）时，必须使用POST方法，并确保使用HTTPS协议。</span>

### 5.2 常见表单控件

#### 文本框

```html
<label for="username">用户名：</label>
<input type="text" id="username" name="username" required>
```

#### 密码框

```html
<label for="password">密码：</label>
<input type="password" id="password" name="password">
```

#### 单选按钮

```html
<input type="radio" id="male" name="gender" value="male">
<label for="male">男</label>
<input type="radio" id="female" name="gender" value="female">
<label for="female">女</label>
```

#### 复选框

```html
<input type="checkbox" id="hobby1" name="hobby" value="reading">
<label for="hobby1">阅读</label>
<input type="checkbox" id="hobby2" name="hobby" value="sports">
<label for="hobby2">运动</label>
```

#### 下拉菜单

```html
<select name="city">
    <option value="beijing">北京</option>
    <option value="shanghai">上海</option>
    <option value="guangzhou">广州</option>
</select>
```

#### 文本域

```html
<textarea name="message" rows="5" cols="30"></textarea>
```

#### 提交按钮

```html
<button type="submit">提交</button>
<input type="submit" value="提交">
```

### 5.3 表单验证

HTML5提供了内置的表单验证功能：

```html
<!-- 必填字段 -->
<input type="text" required>

<!-- 最小长度 -->
<input type="text" minlength="3">

<!-- 最大长度 -->
<input type="text" maxlength="10">

<!-- 邮箱验证 -->
<input type="email" required>

<!-- 数字范围 -->
<input type="number" min="1" max="100">

<!-- 正则表达式 -->
<input type="text" pattern="[a-zA-Z0-9]+">
```

<span class="tip-box">HTML5表单验证可以减少JavaScript代码量，但为了兼容性和安全性，建议同时使用服务端验证。</span>

## 六、HTML5新特性

### 6.1 多媒体元素

#### 视频

```html
<video src="video.mp4" controls width="640" height="360">
    您的浏览器不支持视频播放
</video>
```

#### 音频

```html
<audio src="audio.mp3" controls>
    您的浏览器不支持音频播放
</audio>
```

### 6.2 Canvas绘图

```html
<canvas id="myCanvas" width="200" height="100"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    ctx.fillStyle = 'red';
    ctx.fillRect(10, 10, 50, 50);
</script>
```

<span class="tip-box">Canvas适合绘制图形、动画和游戏，而SVG适合绘制矢量图形。</span>

### 6.3 本地存储

```javascript
// localStorage（持久化存储）
localStorage.setItem('username', '张三');
const username = localStorage.getItem('username');

// sessionStorage（会话存储）
sessionStorage.setItem('token', 'abc123');
const token = sessionStorage.getItem('token');
```

### 6.4 Web Workers

```javascript
// 创建Web Worker
const worker = new Worker('worker.js');

// 发送消息
worker.postMessage('Hello');

// 接收消息
worker.onmessage = function(e) {
    console.log(e.data);
};
```

<span class="warning-box">注意：Web Worker不能访问DOM，只能处理计算密集型任务。</span>

## 七、HTML最佳实践

### 7.1 语义化编码

- 使用合适的语义标签，避免滥用div
- 确保标题层级正确（h1-h6）
- 为图片添加alt属性

### 7.2 可访问性

- 使用label关联表单控件
- 为链接添加title属性
- 使用ARIA属性增强语义

### 7.3 SEO优化

- 使用h1标签作为页面主标题
- 添加meta description
- 使用语义化标签组织内容

### 7.4 性能优化

- 图片使用合适的格式和大小
- 使用懒加载（loading="lazy"）
- 减少HTTP请求

## 八、总结

<span class="important-note">HTML是Web开发的基石，掌握HTML基础知识是学习前端开发的第一步。</span>

通过本教程，你应该了解：

1. HTML文档的基本结构
2. 常用标签的使用方法
3. HTML5语义化标签
4. 表单的创建和验证
5. HTML5的新特性

<span class="tip-box">继续学习CSS和JavaScript，你将能够创建更加丰富和交互性的网页！</span>