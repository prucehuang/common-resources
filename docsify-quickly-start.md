## docsify 是什么？

文档站点生成器

> A magical documentation site generator.
>
> - Simple and lightweight
> - No statically built html files
> - Multiple themes

docsify部署简单，不需要额外的生成很多html文件，比gitbook轻量，问题是index.html配置起来更为复杂，需要维护很多script脚本。

## 快速开始

[官网(docsify.js.org)](https://docsify.js.org/#/zh-cn/quickstart)

### 安装

```text
npm i docsify-cli -g
```

### 初始化

```html
cd xxx
docsify init ./
```

初始化后生成以下文件：

- `index.html`：入口文件
- `README.md`：将作为主页渲染
- `.nojekyll`：阻止 Github Pages 忽略以下划线开头的文件

### 启动服务

```html
docsify serve ./
```

### 路由说明

```html
/README.md        => http://localhost:3000/
/guide.md         => http://localhost:3000/guide.md
/zh-cn/README.md  => http://localhost:3000/zh-cn/
/zh-cn/guide.md   => http://localhost:3000/zh-cn/guide.md
```

## 导航与侧边栏配置

### 导航栏

#### 简单导航栏

简单的导航栏可以在 `index.html` 文件中直接定义：

```html
<body>
  <nav>
    <a href="#/">首页</a>
    <a href="https://www.baidu.com" target="_blank">百度</a>
  </nav>
  <div id="app"></div>
</body>
```

#### 复杂导航

复杂导航可以通过 Markdown 文件配置。

首先配置 `loadNavbar` 为 `true`：

```html
<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//unpkg.com/docsify"></script>
```

在 `./docs` 下创建一个 `_navbar.md` 文件，在该文件中使用 Markdown 格式书写导航：

```text
* 导航1
    * [子导航](nav1/child/)
* [导航2](nav2/)
```

### 侧边栏

默认情况下，侧边栏会根据当前文章的标题生成目录。但也可以通过 Markdown 文档生成。

首先配置 `loadSidebar` 选项为 `true`：

```html
<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//unpkg.com/docsify"></script>
```

然后在 `./docs` 下创建 `_sidebar.md` 文件：

```text
* [简介](/)
* 数据结构
  * [数组](data-structure/array/)
  * [字符串](data-structure/string/)
  * [链表](data-structure/linked_list/)
  * 树
    * [递归](data-structure/tree/recursion/)
    * [层次遍历（BFS）](data-structure/tree/bfs/)
    * [前中后序遍历（DFS）](data-structure/tree/dfs/)
    * [其他](data-structure/tree/other/)
  * [堆](data-structure/heap/)
  * [栈](data-structure/stack/)
  * [哈希表](data-structure/hash/)
* 算法思想
  * 排序
    * [堆排序](algorithm/sort/heap/)
    * [快速排序](algorithm/sort/quick/)
    * [冒泡排序](algorithm/sort/bubble/)
    * [其他](algorithm/sort/other/)
  * 搜索
    * [深度优先](algorithm/research/dfs/)
    * [广度优先](algorithm/research/bfs/)
    * [二分查找](algorithm/research/binary-search/)
  * [动态规划](algorithm/dynamic/)
  * [贪心](algorithm/greedy/)
```

## 插件

### 代码高亮

使用 [Prism](https://link.zhihu.com/?target=https%3A//github.com/PrismJS/prism) 作为代码高亮插件，可以在 `index.html` 中这样配置：

```html
<script src="//unpkg.com/docsify"></script>
<script src="//unpkg.com/prismjs/components/prism-bash.js"></script>
<script src="//unpkg.com/prismjs/components/prism-python.js"></script>
```

------

更多插件见 [插件列表](https://link.zhihu.com/?target=https%3A//docsify.js.org/%23/plugins)。

## 部署到 Github Pages

我的 Github Pages 读取的是 `gh-pages` 分支下的代码，因此我要把 `./docs` 下的文件上传到 `gh-pages` 分支上，完整的代码则上传的到 `master` 分支。