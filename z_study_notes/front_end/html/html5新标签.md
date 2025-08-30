# H5新标签
- 语义化标签
  - header: 头部区域
  - nav: 导航区域
  - section: 章节区域
  - article: 文章区域
  - aside: 侧边栏区域
  - footer: 底部区域
- 结构化布局
  - 使用语义化标签构建网页结构
  - 提高可读性和可维护性
- 示例代码
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML5新标签示例</title>
</head>
<body>
    <header>
        <h1>网站标题</h1>
        <nav>
            <ul>
                <li><a href="#home">首页</a></li>
                <li><a href="#about">关于我们</a></li>
                <li><a href="#services">服务</a></li>
                <li><a href="#contact">联系我们</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section id="home">
            <h2>欢迎来到我们的网站</h2>
            <p>这里是首页内容。</p>
        </section>
        <section id="about">
            <h2>关于我们</h2>
            <p>这里是关于我们的内容。</p>
        </section>
        <section id="services">
            <h2>我们的服务</h2>
            <article>
                <h3>服务一</h3>
                <p>服务一的详细描述。</p>
            </article>
            <article>
                <h3>服务二</h3>
                <p>服务二的详细描述。</p>
            </article>
        </section>
        <aside>
            <h2>侧边栏</h2>
            <p>这里是侧边栏内容。</p>
        </aside>
    </main>
    <footer>
        <p>&copy; 2024 capybara studio. 保留所有权利.</p>
    </footer>
</body>
</html>
```