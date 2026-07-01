# 后端开发实战指南（从零开始）

<span class="important-note">本文档专为零基础学员设计，从环境搭建到项目实战，每一步都配有详细的实操内容。你将学习到 Node.js + Express 后端开发的完整流程，包括 API 开发、数据库操作、项目部署等核心技能。</span>

## 第一章：环境搭建

### 1.1 安装 Node.js

<span class="important-note">Node.js 是运行 JavaScript 的服务器端环境，是后端开发的基础。</span>

**实操步骤：**

1. 打开浏览器，访问 [nodejs.org](https://nodejs.org/)
2. 下载 **LTS 版本**（长期支持版本，更稳定）
3. 双击安装包，按照向导完成安装
4. 验证安装是否成功：

```bash
node -v
npm -v
```

<span class="tip-box">安装成功后会显示 Node.js 版本号和 npm 版本号。npm 是 Node.js 的包管理工具。</span>

### 1.2 安装代码编辑器

**推荐使用 VS Code：**

1. 访问 [code.visualstudio.com](https://code.visualstudio.com/)
2. 下载并安装 VS Code
3. 打开 VS Code，安装以下扩展：
   - Chinese (Simplified) Language Pack
   - ESLint
   - Prettier
   - Node.js Extension Pack

<span class="tip-box">扩展可以大幅提升开发效率，建议全部安装。</span>

### 1.3 创建第一个项目

**实操步骤：**

1. 打开命令行，创建项目文件夹：

```bash
mkdir my-first-backend
cd my-first-backend
```

2. 初始化项目：

```bash
npm init -y
```

3. 查看生成的 package.json 文件：

```json
{
  "name": "my-first-backend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

<div class="warning-box">`npm init -y` 中的 `-y` 表示跳过所有提问，使用默认值。如果想自定义配置，可以不带 `-y`。</div>

## 第二章：基础概念

### 2.1 什么是后端

<span class="important-note">后端（Backend）是指服务器端的程序，负责处理业务逻辑、数据库操作、API 接口等。</span>

**前后端对比：**

| 对比项 | 前端 | 后端 |
|--------|------|------|
| 运行位置 | 浏览器 | 服务器 |
| 主要语言 | HTML/CSS/JavaScript | Node.js/Python/Java 等 |
| 处理内容 | 用户界面 | 业务逻辑 |
| 数据存储 | 本地存储/Cookie | 数据库 |

### 2.2 HTTP 请求与响应

**HTTP 请求方法：**

| 方法 | 用途 | 示例 |
|------|------|------|
| GET | 获取数据 | 查询用户列表 |
| POST | 创建数据 | 注册新用户 |
| PUT | 更新数据 | 修改用户信息 |
| DELETE | 删除数据 | 删除用户 |

**HTTP 状态码：**

| 状态码 | 含义 | 常见场景 |
|--------|------|---------|
| 200 | 请求成功 | 查询成功 |
| 201 | 创建成功 | 新增数据成功 |
| 400 | 请求错误 | 参数错误 |
| 401 | 未授权 | 需要登录 |
| 404 | 未找到 | 请求的资源不存在 |
| 500 | 服务器错误 | 代码逻辑错误 |

<span class="tip-box">记住这些状态码，它们是调试后端程序的重要依据。</span>

### 2.3 路由概念

**路由（Route）** 是指根据 URL 和请求方法，将请求分发到对应的处理函数。

```
URL: /api/users
请求方法: GET
处理函数: getAllUsers()

URL: /api/users/1
请求方法: GET
处理函数: getUserById(1)

URL: /api/users
请求方法: POST
处理函数: createUser()
```

## 第三章：Express 框架入门

### 3.1 安装 Express

```bash
npm install express
```

### 3.2 创建第一个 Express 应用

创建 `index.js` 文件：

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, Backend!');
});

app.listen(port, () => {
  console.log(`服务器运行在 http://localhost:${port}`);
});
```

**运行方式：**

```bash
node index.js
```

打开浏览器访问 `http://localhost:3000`，你会看到 "Hello, Backend!"。

<span class="tip-box">每次修改代码后需要重启服务器，可以使用 `nodemon` 工具实现热重载：`npm install -g nodemon`，然后使用 `nodemon index.js` 运行。</span>

### 3.3 创建多个路由

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('首页');
});

app.get('/about', (req, res) => {
  res.send('关于我们');
});

app.get('/api/users', (req, res) => {
  const users = [
    { id: 1, name: '张三', age: 25 },
    { id: 2, name: '李四', age: 30 },
    { id: 3, name: '王五', age: 28 }
  ];
  res.json(users);
});

app.listen(port, () => {
  console.log(`服务器运行在 http://localhost:${port}`);
});
```

**测试路由：**

1. `http://localhost:3000` - 首页
2. `http://localhost:3000/about` - 关于我们
3. `http://localhost:3000/api/users` - 获取用户列表（JSON 格式）

<span class="tip-box">使用 `res.json()` 返回 JSON 格式数据，这是 API 接口的标准返回格式。</span>

### 3.4 路径参数

```javascript
app.get('/api/users/:id', (req, res) => {
  const userId = parseInt(req.params.id);
  const users = [
    { id: 1, name: '张三', age: 25 },
    { id: 2, name: '李四', age: 30 },
    { id: 3, name: '王五', age: 28 }
  ];
  
  const user = users.find(u => u.id === userId);
  
  if (user) {
    res.json(user);
  } else {
    res.status(404).json({ message: '用户不存在' });
  }
});
```

**测试：**

- `http://localhost:3000/api/users/1` - 返回张三的信息
- `http://localhost:3000/api/users/99` - 返回 404 错误

<span class="warning-box">`req.params.id` 获取到的是字符串类型，需要使用 `parseInt()` 转换为数字。</span>

### 3.5 查询参数

```javascript
app.get('/api/search', (req, res) => {
  const keyword = req.query.keyword;
  const page = parseInt(req.query.page) || 1;
  
  res.json({
    message: '搜索成功',
    keyword: keyword,
    page: page
  });
});
```

**测试：**

- `http://localhost:3000/api/search?keyword=test&page=2`
- 返回：`{"message":"搜索成功","keyword":"test","page":2}`

## 第四章：处理 POST 请求

### 4.1 解析请求体

Express 默认不会解析 POST 请求的请求体，需要使用中间件：

```javascript
const express = require('express');
const app = express();

// 解析 JSON 格式的请求体
app.use(express.json());

// 解析表单格式的请求体
app.use(express.urlencoded({ extended: true }));
```

### 4.2 创建 POST 接口

```javascript
let users = [
  { id: 1, name: '张三', age: 25 }
];

app.post('/api/users', (req, res) => {
  const newUser = {
    id: users.length + 1,
    name: req.body.name,
    age: req.body.age
  };
  
  users.push(newUser);
  
  res.status(201).json({
    message: '用户创建成功',
    user: newUser
  });
});
```

**使用 curl 测试：**

```bash
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"赵六","age":22}'
```

**使用 Postman 测试：**

1. 下载并安装 Postman
2. 新建请求
3. 选择 POST 方法
4. 输入 URL：`http://localhost:3000/api/users`
5. 在 Body 中选择 raw -> JSON
6. 输入：`{"name":"赵六","age":22}`
7. 点击 Send

<span class="tip-box">Postman 是后端开发必备的工具，建议熟练掌握。</span>

## 第五章：数据库操作

### 5.1 安装 SQLite

SQLite 是一个轻量级数据库，无需单独安装服务器，适合初学者。

```bash
npm install sqlite3
```

### 5.2 创建数据库连接

```javascript
const sqlite3 = require('sqlite3').verbose();

// 创建数据库连接
const db = new sqlite3.Database('./mydb.db', (err) => {
  if (err) {
    console.error(err.message);
  }
  console.log('成功连接到 SQLite 数据库');
});

// 创建用户表
db.run(`CREATE TABLE IF NOT EXISTS users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL,
  age INTEGER,
  email TEXT UNIQUE,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP
)`);
```

### 5.3 插入数据

```javascript
app.post('/api/users', (req, res) => {
  const { name, age, email } = req.body;
  
  db.run(
    'INSERT INTO users (name, age, email) VALUES (?, ?, ?)',
    [name, age, email],
    function(err) {
      if (err) {
        return res.status(400).json({ error: err.message });
      }
      res.status(201).json({
        message: '用户创建成功',
        id: this.lastID
      });
    }
  );
});
```

### 5.4 查询数据

```javascript
// 获取所有用户
app.get('/api/users', (req, res) => {
  db.all('SELECT * FROM users', (err, rows) => {
    if (err) {
      return res.status(500).json({ error: err.message });
    }
    res.json(rows);
  });
});

// 根据 ID 查询用户
app.get('/api/users/:id', (req, res) => {
  const id = req.params.id;
  
  db.get('SELECT * FROM users WHERE id = ?', [id], (err, row) => {
    if (err) {
      return res.status(500).json({ error: err.message });
    }
    if (row) {
      res.json(row);
    } else {
      res.status(404).json({ message: '用户不存在' });
    }
  });
});
```

### 5.5 更新数据

```javascript
app.put('/api/users/:id', (req, res) => {
  const id = req.params.id;
  const { name, age, email } = req.body;
  
  db.run(
    'UPDATE users SET name = ?, age = ?, email = ? WHERE id = ?',
    [name, age, email, id],
    function(err) {
      if (err) {
        return res.status(400).json({ error: err.message });
      }
      if (this.changes > 0) {
        res.json({ message: '用户更新成功' });
      } else {
        res.status(404).json({ message: '用户不存在' });
      }
    }
  );
});
```

### 5.6 删除数据

```javascript
app.delete('/api/users/:id', (req, res) => {
  const id = req.params.id;
  
  db.run('DELETE FROM users WHERE id = ?', [id], function(err) {
    if (err) {
      return res.status(500).json({ error: err.message });
    }
    if (this.changes > 0) {
      res.json({ message: '用户删除成功' });
    } else {
      res.status(404).json({ message: '用户不存在' });
    }
  });
});
```

<span class="tip-box">SQLite 适合学习和小型项目，生产环境中常用 MySQL 或 PostgreSQL。</span>

## 第六章：项目结构规范

### 6.1 合理的目录结构

```
my-backend/
├── index.js          # 入口文件
├── package.json
├── node_modules/
├── controllers/      # 控制器（处理请求逻辑）
│   └── userController.js
├── routes/           # 路由定义
│   └── userRoutes.js
├── models/           # 数据模型
│   └── userModel.js
├── middleware/       # 中间件
│   └── auth.js
└── config/           # 配置文件
    └── database.js
```

### 6.2 分离路由和控制器

**routes/userRoutes.js：**

```javascript
const express = require('express');
const router = express.Router();
const userController = require('../controllers/userController');

router.get('/', userController.getAllUsers);
router.get('/:id', userController.getUserById);
router.post('/', userController.createUser);
router.put('/:id', userController.updateUser);
router.delete('/:id', userController.deleteUser);

module.exports = router;
```

**controllers/userController.js：**

```javascript
const userModel = require('../models/userModel');

exports.getAllUsers = (req, res) => {
  userModel.getAll((err, users) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json(users);
  });
};

exports.getUserById = (req, res) => {
  const id = req.params.id;
  userModel.getById(id, (err, user) => {
    if (err) return res.status(500).json({ error: err.message });
    if (user) {
      res.json(user);
    } else {
      res.status(404).json({ message: '用户不存在' });
    }
  });
};

// 其他方法类似...
```

**models/userModel.js：**

```javascript
const db = require('../config/database');

exports.getAll = (callback) => {
  db.all('SELECT * FROM users', callback);
};

exports.getById = (id, callback) => {
  db.get('SELECT * FROM users WHERE id = ?', [id], callback);
};

// 其他方法类似...
```

**index.js：**

```javascript
const express = require('express');
const app = express();
const userRoutes = require('./routes/userRoutes');

app.use(express.json());
app.use('/api/users', userRoutes);

app.listen(3000, () => {
  console.log('服务器运行在 http://localhost:3000');
});
```

<span class="tip-box">按照 MVC 架构分离代码，项目更易于维护和扩展。</span>

## 第七章：中间件

### 7.1 什么是中间件

中间件（Middleware）是在请求处理流程中执行的函数，可以访问请求对象、响应对象和下一个中间件。

```javascript
app.use((req, res, next) => {
  console.log('请求时间:', new Date().toISOString());
  next(); // 调用下一个中间件
});
```

### 7.2 常用中间件

**日志中间件：**

```javascript
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```

**错误处理中间件：**

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: '服务器内部错误' });
});
```

**认证中间件：**

```javascript
const authenticate = (req, res, next) => {
  const token = req.headers.authorization;
  
  if (!token) {
    return res.status(401).json({ message: '未授权' });
  }
  
  // 验证 token...
  next();
};

// 使用认证中间件
app.get('/api/protected', authenticate, (req, res) => {
  res.json({ message: '这是受保护的内容' });
});
```

## 第八章：项目实战 - Todo 应用

### 8.1 需求分析

创建一个简单的 Todo 应用，包含以下功能：
- 创建 Todo
- 获取所有 Todo
- 更新 Todo
- 删除 Todo
- 标记 Todo 完成状态

### 8.2 创建项目

```bash
mkdir todo-app
cd todo-app
npm init -y
npm install express sqlite3
```

### 8.3 完整代码

**index.js：**

```javascript
const express = require('express');
const sqlite3 = require('sqlite3').verbose();
const app = express();
const port = 3000;

app.use(express.json());

// 数据库连接
const db = new sqlite3.Database('./todo.db', (err) => {
  if (err) console.error(err.message);
  console.log('数据库连接成功');
});

// 创建表
db.run(`CREATE TABLE IF NOT EXISTS todos (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  title TEXT NOT NULL,
  description TEXT,
  completed BOOLEAN DEFAULT 0,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  updated_at DATETIME DEFAULT CURRENT_TIMESTAMP
)`);

// 获取所有 Todo
app.get('/api/todos', (req, res) => {
  db.all('SELECT * FROM todos ORDER BY created_at DESC', (err, rows) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json(rows);
  });
});

// 获取单个 Todo
app.get('/api/todos/:id', (req, res) => {
  db.get('SELECT * FROM todos WHERE id = ?', [req.params.id], (err, row) => {
    if (err) return res.status(500).json({ error: err.message });
    if (row) res.json(row);
    else res.status(404).json({ message: 'Todo 不存在' });
  });
});

// 创建 Todo
app.post('/api/todos', (req, res) => {
  const { title, description } = req.body;
  
  if (!title) {
    return res.status(400).json({ message: '标题不能为空' });
  }
  
  db.run(
    'INSERT INTO todos (title, description) VALUES (?, ?)',
    [title, description],
    function(err) {
      if (err) return res.status(400).json({ error: err.message });
      res.status(201).json({ id: this.lastID, title, description });
    }
  );
});

// 更新 Todo
app.put('/api/todos/:id', (req, res) => {
  const { title, description, completed } = req.body;
  
  db.run(
    'UPDATE todos SET title = ?, description = ?, completed = ?, updated_at = CURRENT_TIMESTAMP WHERE id = ?',
    [title, description, completed, req.params.id],
    function(err) {
      if (err) return res.status(400).json({ error: err.message });
      if (this.changes > 0) res.json({ message: '更新成功' });
      else res.status(404).json({ message: 'Todo 不存在' });
    }
  );
});

// 删除 Todo
app.delete('/api/todos/:id', (req, res) => {
  db.run('DELETE FROM todos WHERE id = ?', [req.params.id], function(err) {
    if (err) return res.status(500).json({ error: err.message });
    if (this.changes > 0) res.json({ message: '删除成功' });
    else res.status(404).json({ message: 'Todo 不存在' });
  });
});

// 错误处理
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: '服务器错误' });
});

app.listen(port, () => {
  console.log(`服务器运行在 http://localhost:${port}`);
});
```

### 8.4 测试 API

使用 Postman 测试以下接口：

| 方法 | 接口 | 功能 |
|------|------|------|
| GET | /api/todos | 获取所有 Todo |
| GET | /api/todos/1 | 获取 ID 为 1 的 Todo |
| POST | /api/todos | 创建新 Todo |
| PUT | /api/todos/1 | 更新 ID 为 1 的 Todo |
| DELETE | /api/todos/1 | 删除 ID 为 1 的 Todo |

**POST 请求示例：**

```json
{
  "title": "学习 Node.js",
  "description": "完成后端开发实战指南的学习"
}
```

**PUT 请求示例：**

```json
{
  "title": "学习 Node.js",
  "description": "完成后端开发实战指南的学习",
  "completed": 1
}
```

<span class="tip-box">完成这个项目后，你已经掌握了后端开发的核心技能，可以尝试添加更多功能，如分页、搜索、用户认证等。</span>

## 第九章：部署上线

### 9.1 准备工作

1. 在 [render.com](https://render.com/) 或 [vercel.com](https://vercel.com/) 注册账号
2. 将项目推送到 GitHub
3. 配置环境变量

### 9.2 使用 Render 部署

1. 登录 Render
2. 点击 "New +" -> "Web Service"
3. 选择 GitHub 仓库
4. 配置构建命令：`npm install`
5. 配置启动命令：`node index.js`
6. 设置环境变量（如果需要）
7. 点击 "Deploy"

### 9.3 使用 Vercel 部署

1. 登录 Vercel
2. 点击 "New Project"
3. 导入 GitHub 仓库
4. 配置项目设置
5. 点击 "Deploy"

<span class="warning-box">部署前确保项目可以在本地正常运行，检查依赖是否完整。</span>

## 总结

<span class="important-note">恭喜你完成了后端开发实战指南的学习！你已经掌握了：</span>

1. ✅ Node.js 环境搭建
2. ✅ Express 框架基础
3. ✅ RESTful API 开发
4. ✅ SQLite 数据库操作
5. ✅ 项目结构规范
6. ✅ 中间件使用
7. ✅ Todo 项目实战
8. ✅ 项目部署上线

<span class="tip-box">下一步学习建议：</span>

1. **学习更多数据库**：MySQL、PostgreSQL、MongoDB
2. **用户认证**：JWT、OAuth
3. **API 文档**：Swagger/OpenAPI
4. **测试**：Jest、Mocha
5. **缓存**：Redis
6. **消息队列**：RabbitMQ

持续练习，多写项目，你一定能成为优秀的后端开发者！