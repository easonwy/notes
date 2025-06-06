# HTML 超文本标记语言

## 概述
HTML (HyperText Markup Language) 是一种用于创建网页的标准标记语言，描述网页的结构和语义。

## 基本结构
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML文档</title>
</head>
<body>
    <header>
        <h1>标题</h1>
        <nav>导航</nav>
    </header>
    <main>
        <article>
            <h2>文章标题</h2>
            <p>段落内容</p>
        </article>
    </main>
    <footer>
        <p>页脚内容</p>
    </footer>
</body>
</html>
```

## 常用元素
1. 文本元素
   - `<h1>` - `<h6>`: 标题
   - `<p>`: 段落
   - `<span>`: 内联文本
   - `<strong>`, `<em>`: 强调

2. 列表元素
   - `<ul>`: 无序列表
   - `<ol>`: 有序列表
   - `<li>`: 列表项
   - `<dl>`, `<dt>`, `<dd>`: 定义列表

3. 表单元素
   - `<form>`: 表单
   - `<input>`: 输入框
   - `<select>`: 下拉选择
   - `<textarea>`: 多行文本

## 语义化标签
1. 结构标签
   - `<header>`
   - `<nav>`
   - `<main>`
   - `<article>`
   - `<section>`
   - `<footer>`

2. 多媒体标签
   - `<img>`
   - `<video>`
   - `<audio>`
   - `<canvas>`

## 最佳实践
1. 文档结构
   - 清晰的层次
   - 语义化标签
   - 适当的注释

2. 可访问性
   - ARIA属性
   - 替代文本
   - 键盘导航

3. SEO优化
   - Meta标签
   - 标题层级
   - 结构化数据

## HTML5新特性
1. 新增语义标签
2. 表单增强
3. 多媒体支持
4. 本地存储
5. WebSocket

## 参考资料
1. [MDN HTML Guide](https://developer.mozilla.org/en-US/docs/Web/HTML)
2. [HTML Living Standard](https://html.spec.whatwg.org/)
3. [W3Schools HTML Tutorial](https://www.w3schools.com/html/)
