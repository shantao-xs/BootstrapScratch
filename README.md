# Bootstrap v5 from scratch
## todo
能不能做一个交互式的doc，点击哪个部分就显示对应代码？现在还是不够直观
 
## Intro
本项目为参照[该快速入门课程](https://gitee.com/MASUKA/bootstrap5_2021)的练手自习

## toolkit
具体toolkit参见<mark>前端toolkit集合 tbc</mark>
### 1. skeleton: html
插件：
- Emmet - 快捷填充代码
    - ! 生成html页面框架
    - .test 
### 2. css: bootstrap
引入[bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/)的js和cs文件，把script放到到\<body>底部

## Web Details
注意：
1. 每一个大模块(\<section>或\<nav>)，都需要用\<container>框住边框 
2. 框架思路：组块化，模块中的每个小组块用div来框住区隔 

### 1. 导航栏 \<nav>
1. 统一边距：一个模块用一个\<container>框住
2. 自适应页面：为不同页面大小设置不同的页面呈现效果
    - 对页边距>960px: 并排式按钮 *navbar-collapse + ul/li* 
    - <960px：下拉式按钮 *navbar-toggler*


### 2. 主海报 \<section>
1. 统一边距：使用bootstrap提供的底层样式
2. 自适应页面：小页面不显示海报图


页面整体需要响应式设计

<mark>功能uml如下：tbc</mark>

## Bootstrap入门
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