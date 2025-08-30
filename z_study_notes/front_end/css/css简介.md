CSS（层叠样式表）是让网页变得美观的核心技术。让我们开始这段精彩的旅程！

---

# CSS 入门全面指南

## 1. 什么是CSS？

**CSS**（Cascading Style Sheets，层叠样式表）是一种用于**描述HTML文档表现样式**的语言。它控制网页的布局、颜色、字体、动画等视觉表现。

### 核心概念：
- **结构与表现分离**：HTML负责结构，CSS负责样式
- **层叠性**：多个样式规则可以应用于同一元素，按特定规则层叠
- **继承性**：某些样式属性可以从父元素继承给子元素

## 2. 三种引入CSS的方式

### 1) 内联样式（Inline Styles）
直接在HTML元素的`style`属性中编写（不推荐大量使用）
```html
<p style="color: blue; font-size: 16px;">这是一个段落</p>
```

### 2) 内部样式表（Internal Style Sheet）
在HTML文档的`<head>`中使用`<style>`标签
```html
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }
    </style>
</head>
```

### 3) 外部样式表（External Style Sheet）✅ **推荐方式**
在单独的`.css`文件中编写，然后在HTML中链接
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```
在`styles.css`文件中：
```css
p {
    color: blue;
    font-size: 16px;
}
```

## 3. CSS基本语法结构

```css
选择器 {
    属性: 值;
    属性: 值;
}
```

**示例：**
```css
h1 {
    color: #333;           /* 文字颜色 */
    font-size: 2em;        /* 字体大小 */
    margin-bottom: 20px;   /* 下边距 */
    text-align: center;    /* 文本对齐 */
}
```

## 4. 常用选择器（Selector）

### 基本选择器
| 选择器 | 示例 | 描述 |
| :--- | :--- | :--- |
| **元素选择器** | `p` | 选择所有 `<p>` 元素 |
| **类选择器** | `.classname` | 选择 `class="classname"` 的元素 |
| **ID选择器** | `#idname` | 选择 `id="idname"` 的元素 |
| **通用选择器** | `*` | 选择所有元素 |

### 组合选择器
| 选择器 | 示例 | 描述 |
| :--- | :--- | :--- |
| **后代选择器** | `div p` | 选择 `<div>` 内的所有 `<p>` |
| **子元素选择器** | `div > p` | 选择直接子元素 `<p>` |
| **相邻兄弟选择器** | `h1 + p` | 选择紧接在 `<h1>` 后的 `<p>` |
| **通用兄弟选择器** | `h1 ~ p` | 选择所有在 `<h1>` 后的 `<p>` |

### 属性选择器
```css
a[target] { }              /* 有target属性的<a> */
a[target="_blank"] { }     /* target="_blank"的<a> */
a[href^="https"] { }       /* href以"https"开头的<a> */
a[href$=".pdf"] { }        /* href以".pdf"结尾的<a> */
a[href*="example"] { }     /* href包含"example"的<a> */
```

## 5. 常用CSS属性

### 文本样式
```css
p {
    color: #333333;            /* 文字颜色 */
    font-family: Arial, sans-serif; /* 字体栈 */
    font-size: 16px;           /* 字体大小 */
    font-weight: bold;         /* 字重：normal, bold, 100-900 */
    font-style: italic;        /* 字体样式：italic, normal */
    text-align: center;        /* 对齐：left, center, right, justify */
    text-decoration: underline;/* 装饰：underline, none, line-through */
    line-height: 1.6;          /* 行高 */
    letter-spacing: 1px;       /* 字母间距 */
}
```

### 盒模型（Box Model）
每个元素都是一个盒子，包含：
- **内容（Content）**
- **内边距（Padding）**
- **边框（Border）**
- **外边距（Margin）**

```css
.box {
    width: 300px;           /* 内容宽度 */
    height: 200px;          /* 内容高度 */
    padding: 20px;          /* 内边距 */
    border: 2px solid #000; /* 边框：宽度 样式 颜色 */
    margin: 30px;           /* 外边距 */
    
    /* 使用box-sizing更直观地控制尺寸 */
    box-sizing: border-box; /* content-box | border-box */
}
```

### 背景样式
```css
.element {
    background-color: #f0f0f0;      /* 背景颜色 */
    background-image: url('bg.jpg'); /* 背景图片 */
    background-repeat: no-repeat;   /* 重复方式：repeat, no-repeat, repeat-x */
    background-position: center;    /* 位置：top, center, bottom, left, right */
    background-size: cover;         /* 尺寸：cover, contain, 具体值 */
    
    /* 简写形式 */
    background: #f0f0f0 url('bg.jpg') no-repeat center/cover;
}
```

### 布局属性
```css
.container {
    display: block;         /* 显示方式：block, inline, inline-block, none */
    display: flex;          /* 弹性布局 */
    display: grid;          /* 网格布局 */
    
    position: static;       /* 定位：static, relative, absolute, fixed, sticky */
    position: relative;
    top: 10px;
    left: 20px;
    
    float: left;            /* 浮动：left, right, none */
    clear: both;            /* 清除浮动：left, right, both */
}
```

## 6. 实用示例

### 示例1：基础样式设置
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>CSS基础示例</title>
    <style>
        /* 重置默认样式 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f4f4f4;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 30px;
            font-size: 2.5em;
        }
        
        .card {
            background: #ecf0f1;
            padding: 20px;
            margin: 15px 0;
            border-left: 4px solid #3498db;
            border-radius: 4px;
        }
        
        .card h2 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .btn {
            display: inline-block;
            background: #3498db;
            color: white;
            padding: 10px 20px;
            text-decoration: none;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background: #2980b9;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>欢迎学习CSS</h1>
        
        <div class="card">
            <h2>CSS的力量</h2>
            <p>CSS可以让你的网页变得美观而专业。通过简单的样式规则，你可以控制布局、颜色、字体等所有视觉表现。</p>
        </div>
        
        <div class="card">
            <h2>开始学习</h2>
            <p>从选择器、盒模型到Flexbox和Grid布局，一步步掌握CSS的强大功能。</p>
            <a href="#" class="btn">开始学习</a>
        </div>
    </div>
</body>
</html>
```

### 示例2：简单的响应式布局
```css
/* 响应式设计示例 */
@media (max-width: 768px) {
    .container {
        padding: 15px;
        margin: 10px;
    }
    
    h1 {
        font-size: 2em;
    }
    
    .card {
        margin: 10px 0;
    }
}

@media (max-width: 480px) {
    body {
        padding: 10px;
    }
    
    h1 {
        font-size: 1.5em;
    }
    
    .btn {
        display: block;
        width: 100%;
        text-align: center;
    }
}
```

## 7. 学习路径建议

1.  **基础阶段**：
    - 选择器和基本样式
    - 盒模型和布局基础
    - 文本和背景样式

2.  **进阶阶段**：
    - Flexbox布局
    - Grid布局
    - 响应式设计（媒体查询）
    - 过渡和动画

3.  **高级阶段**：
    - CSS变量（Custom Properties）
    - 现代CSS特性（Grid、Flexbox高级用法）
    - CSS架构（BEM、SMACSS）
    - 预处理器（Sass/Less）

## 8. 最佳实践

1.  **使用外部样式表**：保持HTML和CSS分离
2.  **使用语义化类名**：`.btn-primary` 而不是 `.blue-button`
3.  **移动优先**：先为移动设备设计，再用媒体查询适配大屏幕
4.  **使用CSS重置**：消除浏览器默认样式差异
5.  **保持代码组织**：使用注释和合理的结构

```css
/* ===== 重置样式 ===== */
* { box-sizing: border-box; margin: 0; padding: 0; }

/* ===== 基础样式 ===== */
body { font-family: system-ui, sans-serif; line-height: 1.6; }

/* ===== 组件样式 ===== */
.btn { /* 按钮样式 */ }
.card { /* 卡片样式 */ }

/* ===== 工具类 ===== */
.text-center { text-align: center; }
.mt-20 { margin-top: 20px; }

/* ===== 响应式设计 ===== */
@media (max-width: 768px) { /* 移动端样式 */ }
```

接下来，您想先深入学习CSS的哪个特定领域呢？比如选择器的更多细节、盒模型、或者直接开始学习Flexbox布局？