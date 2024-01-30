# Bootstrap v5 from scratch
## TODO
能不能做一个交互式的doc，点击哪个部分就显示对应代码？现在还是不够直观
 
## Intro
本项目为参照[该快速入门课程](https://gitee.com/MASUKA/bootstrap5_2021)的练手自习

## Toolkit
具体toolkit参见<mark>前端toolkit集合 tbc</mark>
### 1. skeleton: html
插件：
- Emmet - 快捷填充代码
    - ! 生成html页面框架
    - .test 
### 2. css: bootstrap
引入[bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/)的js和cs文件，把script放到到\<body>底部

## Chapter Ⅰ 入门：搭建sections与bootstrap基础样式
### Core Notion：
**1. 页面模块化，模块组块化**：模块中的每个小组块用div来框住区隔   
**2. 响应式设计** 

<br>

### 0. 每个模块需考虑：
1. 各个组块的边距padding, border, margin, etc.
2. 背景颜色与文字颜色
3. 元素的对齐方式（文字、图片等）
4. 响应式设计下的变化
5. 模块下各个小组件的layout（如并排等分）

#### 编写步骤
1. section大框架
2. **container**框住固定样式
3. div设置整个sec的样式
4. 每个组块的具体布局：分成左、右部分？分别设置具体的元素及其样式  
    - **怎么设计layout?**  
    1. 弹性格子布局，左右排列，d-flex
    2. 栅格布局+卡片化，一行12列，设置每个组块可占的列数，class=row, class=col
    - 如：中页面时两两并排、大页面时四四并排则需要每个card占6/4格，即`col-md-6,col-lg-3`
    - 卡片化：card,card-title,card-body,card-tex
5. 对每个组块进行响应式设计
    - Q: 什么情况下切换设计呈现？  
    *A: 在页面大小分别为sm-md-lg-xl-xxl的时候，页面应呈现什么变化？  
    使用<{元素名称}-{页面大小}-block>等方式来调节不同大小的呈现*
    - Q: 怎么写页面大小的条件？  
    *A: div和img可以直接用md等设置条件，p等元素则需要自己把条件写在style.css里，如`@media (min-width: 768px)`*  


### 1. 导航栏\<nav>
1. 统一边距：一个模块用一个\<container>框住
2. 自适应页面：为不同页面大小设置不同的页面呈现效果
    - 对页边距>960px: 并排式按钮 *navbar-collapse + ul/li* 
    - <960px：下拉式按钮 *navbar-toggler*
3. 导航栏固定在页面顶部，并避免挡住下面的section：
    - 固定在顶部：fixed-top
    - 不挡住section：在css里增加一个body::before伪元素
    - *怎么知道导航栏有多高？用开发者工具看它的height*


### 2. 主海报\<section>
1. 统一边距：使用bootstrap提供的底层样式
2. 自适应页面：小页面不显示海报图

### 3. 注册区
1. 弹性格子布局
2. 自适应页面
    - 自适应条件：当页面>min width时，button要是原始大小的50%；否则100%
    - 对非div块组件设计自适应条件：写在style.css里并引入class

### 4. 栏目区
1. 栅格化+卡片化
    - 一个row里三个col，每个col平均大小，横向排列：class=row, class=col
    - 每个col里卡片化：card,card-title,card-body,card-text
3. 自适应页面：大页面横向，小页面纵向排列：col-md

### 5. 相关简介1&2
1. 栅格化+自适应：两个卡片组块水平垂直、居中分布，大页面左右分布，小页面上下分布，左图右字

### 6. 常见问题（利用bootstrap已有组件）
1. Accordion组件：从bootstrap中复制
2. Accordion组件优化：想要第一个下拉框的解答文本默认展开，可以增加class=show

### 7. 讲师介绍
1. 栅格系统+卡片化：大页面并排，中页面两两一排，小页面垂直排列

### 8. 联系我们（利用bootstrap已有组件）
1. list group组件：从bootstrap中复制

### 9. 页脚 \<footer>
1. 具体格式参上

<br>

## Chapter Ⅱ 编译：自定义bootstrap样式






## Bootstrap Docs
具体bootstrap常用内容参见<mark>bootstrap docs整理 tbc</mark>和官方文档  
如导航栏模块：
### navbar
**1. navbar基础**  
示例：
```html
<nav class="navbar navbar-expand-lg bg-dark navbar-dark">
```
- navbar-expand{-sm|-md|-lg|-xl}：响应式设计中用来判定何时切换大小菜单的节点
    - sm:
    - md:
    - lg:
    - xl:
- bg-dark: 背景暗色
- navbar-dark: 暗色主题
  
**2. logo**  
- navbar-brand
    - 文字：`<a href="#" class="navbar-brand">此处输入文字</a>`
    - 图片：`<a href="#" class="navbar-brand"><img src="插入图片地址"></a>`

**3. 小页面菜单**  
示例：
```html
<button 
    class="navbar-toggler" 
    type="button" 
    data-bs-toggle="collapse" 
    data-bs-target="#navmenu">
    <span class="navbar-toggler-icon"></span>
</button>
```
\<button>toggler：
- navbar-toggler: 小页面toggler的样式
- data-bs-toggle: *js* 折叠功能
- data-bs-target: *js* 折叠功能的目标对象是？(id=navmenu)  

\<span>toggler中的图标：
- navbar-toggler-icon：toggler的图标  
  
<br>

**4. 大页面菜单**  
示例：
```html
<div class="collapse navbar-collapse" id="navmenu">
    <ul class="navbar-nav ms-auto">
        <li class="nav-item">
            <div class="nav-link">导航按钮A</div>
        </li>
    </ul>
</div>
```
\<div>大框：
- collapse: 切换大小菜单何时collapse & rebuild
- navbar-collapse: 水平铺满  

\<ul>导航栏列表：
- navbar-nav: 导航栏的样式
- me-auto/ms-auto: 元素居左/居右   

\<li>导航栏细项：
- nav-item:导航item的样式  

\<div>导航栏细项的超链接：
- nav-link:导航栏细项的超链接样式

## 关于设计
可以通过tailwind，bootstrap等的底层样式快速开发，也可以遵循设计准则来自定义设计
### 设计系统-尺寸
尺寸原理：
### 设计系统-颜色
配色问题：