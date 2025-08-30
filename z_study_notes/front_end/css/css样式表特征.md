理解CSS的这些核心特性是掌握CSS的关键。这些特性决定了当多个样式规则冲突时，浏览器应该如何应用它们。

---

# CSS 核心特性详解

## 1. 继承性（Inheritance）

### 什么是继承性？
某些CSS属性会自动从父元素传递到子元素，而不需要显式地为每个子元素设置。

### 可继承的属性
主要是**文本相关**的属性：
- `font-family`、`font-size`、`font-weight`
- `color`、`text-align`、`text-indent`
- `line-height`、`letter-spacing`、`word-spacing`
- `visibility`、`cursor`
- `list-style`（列表相关）

### 不可继承的属性
主要是**布局和盒模型**相关的属性：
- `width`、`height`、`margin`、`padding`
- `border`、`background`、`display`
- `position`、`float`、`clear`
- `overflow`、`z-index`

### 继承示例
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <style>
        body {
            font-family: Arial, sans-serif; /* 会被继承 */
            color: #333;                   /* 会被继承 */
            line-height: 1.6;              /* 会被继承 */
        }
        
        .container {
            border: 2px solid blue;        /* 不会被继承 */
            padding: 20px;                 /* 不会被继承 */
            margin: 20px;                  /* 不会被继承 */
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>标题</h1>
        <p>段落文字会继承body的字体、颜色和行高，但不会继承border、padding和margin。</p>
        <ul>
            <li>列表项1</li>
            <li>列表项2</li>
        </ul>
    </div>
</body>
</html>
```

### 控制继承
```css
.child {
    color: inherit;     /* 显式继承父元素的color */
    font-size: inherit; /* 显式继承父元素的font-size */
    
    color: initial;     /* 重置为属性的初始值 */
    all: initial;       /* 重置所有属性为初始值 */
    
    color: unset;       /* 如果是可继承属性则继承，否则重置为初始值 */
}
```

## 2. 层叠性（Cascading）

### 什么是层叠性？
当多个CSS规则应用于同一个元素时，浏览器会根据一定的规则来决定使用哪个样式。

### 层叠规则
浏览器通过以下三个因素来解决样式冲突：
1. **来源重要性**（Source & Importance）
2. **特异性**（Specificity）
3. **出现顺序**（Order）

## 3. 优先级（Specificity）

### 特异性计算规则
特异性是一个权重系统，用于确定哪个样式声明最终被应用。

#### 特异性权重等级（从高到低）：
1. **内联样式**（1000） - `style="color: red;"`
2. **ID选择器**（0100） - `#header`
3. **类选择器、属性选择器、伪类**（0010）
    - `.class`、`[type="text"]`、`:hover`、`:nth-child()`
4. **元素选择器、伪元素**（0001）
    - `div`、`p`、`::before`、`::after`
5. **通用选择器**（0000） - `*`

**注意**：`!important` 会覆盖所有特异性规则

### 特异性计算示例
```css
/* 特异性: 0,0,0,1 = 1 */
p { color: black; }

/* 特异性: 0,0,1,0 = 10 */
.text { color: blue; }

/* 特异性: 0,0,1,1 = 11 */
p.text { color: green; }

/* 特异性: 0,1,0,0 = 100 */
#main { color: red; }

/* 特异性: 0,1,1,1 = 111 */
div#main p.text { color: purple; }

/* 内联样式: 1,0,0,0 = 1000 */
<p style="color: orange;">文字</p>
```

### 特异性实战
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <style>
        /* 特异性: 1 - 元素选择器 */
        p { color: black; }
        
        /* 特异性: 10 - 类选择器 */
        .special { color: blue; }
        
        /* 特异性: 11 - 类+元素 */
        p.special { color: green; }
        
        /* 特异性: 100 - ID选择器 */
        #unique { color: red; }
        
        /* 特异性: 1,0,0,0 - 内联样式 */
        /* <p style="color: orange;"> */
    </style>
</head>
<body>
    <p>黑色文字（元素选择器）</p>
    <p class="special">绿色文字（p.special胜出）</p>
    <p class="special" id="unique">红色文字（ID选择器胜出）</p>
    <p class="special" id="unique" style="color: orange;">
        橙色文字（内联样式胜出）
    </p>
</body>
</html>
```

## 4. !important 规则

### 使用 !important
`!important` 会覆盖所有其他声明，包括内联样式。

```css
.button {
    background-color: blue !important;
    color: white !important;
}
```

### !important 的最佳实践
**尽量避免使用**，因为：
1. 破坏了层叠的自然流程
2. 使得调试困难
3. 难以覆盖

**仅在以下情况使用**：
- 覆盖第三方库的样式
- 处理浏览器兼容性 hack
- 处理最高优先级的实用类

## 5. 来源重要性层次

浏览器按以下顺序应用样式（从低到高优先级）：

1. **用户代理样式**（浏览器默认样式）
2. **用户样式**（用户自定义的浏览器样式）
3. **作者样式**（开发者写的CSS）
4. **作者样式中的 `!important`**
5. **用户样式中的 `!important`**
6. **用户代理样式中的 `!important`**

## 6. 综合示例

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <style>
        /* 用户代理样式（浏览器默认） */
        /* p { margin: 1em 0; color: black; } */
        
        /* 作者样式 */
        p { color: blue; }                          /* 特异性: 1 */
        
        .content p { color: green; }                /* 特异性: 2 */
        
        #main .text { color: purple; }              /* 特异性: 110 */
        
        .text { color: red !important; }            /* !important */
        
        /* 最终颜色：red (!important胜出) */
    </style>
</head>
<body>
    <div id="main" class="content">
        <p class="text">这段文字的颜色由层叠规则决定</p>
    </div>
</body>
</html>
```

## 7. 解决样式冲突的实战技巧

### 1. 增加特异性
```css
/* 而不是直接使用 !important */
.nav li.active { }    /* 特异性: 21 */
```

### 2. 调整源代码顺序
```css
/* 后面的样式会覆盖前面的 */
.btn { background: blue; }
.btn-primary { background: red; } /* 这个生效 */
```

### 3. 使用CSS自定义属性（变量）
```css
:root {
    --main-color: blue;
}

.element {
    color: var(--main-color);
}
```

### 4. 使用现代CSS特性
```css
/* 使用 :where() 降低特异性 */
:where(.container) p { color: blue; }

/* 使用 :is() 保持特异性 */
:is(.container) p { color: blue; }
```

## 8. 调试工具的使用

在浏览器开发者工具中，可以看到特异性的计算：

1. 打开开发者工具（F12）
2. 选择元素
3. 查看Styles面板
4. 浏览器会显示哪个样式被应用以及为什么

## 总结记忆口诀

**继承文本不继承盒，**
**层叠要看三方面：**
**来源重要特异性，**
**最后才看顺序排。**

**特异性算权重：**
**内联千位ID百，**
**类属性伪十分位，**
**元素伪元个位来。**

理解了这些核心特性，你就能预测和控制CSS的表现行为，写出更健壮、可维护的样式代码！