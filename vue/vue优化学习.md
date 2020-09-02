<!--
 * @Author: your name
 * @Date: 2020-08-21 16:07:08
 * @LastEditTime: 2020-08-21 16:13:11
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Metshare\vue\vue优化学习.md
-->

# 1. 你都做过哪些 Vue 的性能优化？

> - 编码阶段

> - 尽量减少 data 中的数据，data 中的数据都会增加 getter 和 setter，会收集对应的 watcher
> - 如果需要使用 v-for 给每项元素绑定事件时使用事件代理
> - SPA 页面采用 keep-alive 缓存组件
> - 在更多的情况下，使用 v-if 替代 v-show
> - key 保证唯一
> - 使用路由懒加载、异步组件
> - 防抖、节流
> - 第三方模块按需导入
> - 长列表滚动到可视区域动态加载
> - 图片懒加载
> - SEO 优化
> - 预渲染
> - 服务端渲染 SSR
> - 打包优化
> - 压缩代码
> - Tree Shaking/Scope Hoisting
> - 使用 cdn 加载第三方模块
> - 多线程打包 happypack
> - splitChunks 抽离公共文件
> - sourceMap 优化
> - 用户体验
> - 骨架屏
> - PWA
> - 还可以使用缓存(客户端缓存、服务端缓存)优化、服务端开启 gzip 压缩等。
> - (优化是个大工程，会涉及很多方面，这里申请另开一个专栏)

# 2. 前端如何进行 seo 优化

> - 合理的 title、description、keywords：搜索对着三项的权重逐个减小，title 值强调重点即可；description 把页面内容高度概括，不可过分堆砌关键词；keywords 列举出重要关键词。

> - 语义化的 HTML 代码，符合 W3C 规范：语义化代码让搜索引擎容易理解网页
> - 重要内容 HTML 代码放在最前：搜索引擎抓取 HTML 顺序是从上到下，保证重要内容一定会被抓取
> - 重要内容不要用 js 输出：爬虫不会执行 js 获取内容
> - 少用 iframe：搜索引擎不会抓取 iframe 中的内容
> - 非装饰性图片必须加 alt
> - 提高网站速度：网站速度是搜索引擎排序的一个重要指标

# 3. 1000-div 问题

## 一次性插入 1000 个 div，如何优化插入的性能

> - 使用 Fragment

> - var fragment = document.createDocumentFragment();
> - fragment.appendChild(elem);
> - 向 1000 个并排的 div 元素中，插入一个平级的 div 元素，如何优化插入的性能
> - 先 display:none 然后插入 再 display:block
> - 赋予 key，然后使用 virtual-dom，先 render，然后 diff，最后 patch
> - 脱离文档流，用 GPU 去渲染，开启硬件加速
