---
title: "CSS知识总结"
date: 2019-10-27T14:15:01+08:00
draft: false
---

一、 浏览器渲染原理

1.  根据 HTML 构建 HTML 树（DOM）
2.  根据 CSS 构建 CSS 树（CSSOM）
3.  将两棵树合并成一颗渲染树（render tree)
4.  Layout 布局 （文档流、盒模型、计算大小和位置）
5.  Paint 绘制（把边框颜色、文字颜色、阴影等画出来）
6.  Composite 合成（根据层叠关系展示画面）

二、 CSS 动画 transition

1. transform

   - 语法：
     ```
     transform:translate(-50%, -50%)
     ```
   - 组合使用

     ```
     transform: scale(0.5) translate(-100%,-100%)
     ```

     - transform: none; 取消所有效果

   * translate（位移）

     - translateX()
     - translateY()
     - translate()
     - translateZ()
     - translate3d()

   * scale（缩放）

     - scaleX()
     - scaleY()
     - scale()

   * rotate（旋转）

     - rotate()
     - rotateZ()
     - rotateX()
     - rotateY()
     - rotate3d()

   * skew（倾斜）

     - skewX()
     - skewY()
     - skew()

   - **注意**：inline 元素不支持 transform

2. transition

   - 语法：transition: 属性名 时长 过渡方式 延迟

   ```
    transition: left 200ms linear;
   ```

   - 可以用逗号分隔两个不同的属性
     ```
     transition: left 200ms, top 300ms;
     ```

   * 可以用 all 代表所有属性
   * 过渡方式：
     - linear 线性
     - ease
     - ease-in 淡入
     - ease-out 淡出
     - ease-in-out 淡入淡出
     - cubic-bezier
     - step-start
     - step-end
     - steps

   - **注意**：并不是所有属性都能过渡

     - display:none => block 无法过渡

     - 使用 visibility:hidden => visible 代替 display:none => block 的过渡

     - background 颜色可以过渡

     - opacity 透明度可以过渡

- 红心实例：http://js.jirengu.com/hoqog/2/edit

三、 CSS 动画 animation

- 语法： animation: 时长 | 过渡方式 | 延迟 | 次数 | 方向 | 填充模式 | 是否暂停 | 动画名;

- 属性：

  - 时长：1s 或者 1000ms
  - 过渡方式：跟 transition 取值一样，如 linear
  - 次数：3 或者 2.4 或者 infinite
  - 方向：reverse | alternate |alternate-reverse
  - 填充模式：none | forwards |backwards | both
  - 是否暂停：paused | running

  * 红心实例：http://js.jirengu.com/pepok/1/edit?html,css,output

四、@keyframes

- 语法：
  ```
  @keyframes slidein {
    from { transform: translateX(0%);}
    to {transform: translateX(100%);}
  }
  ```
  ```
  @keyframes indentifier {
    0% { top: 0; left:0;}
    30% { top: 50px;}
    68% 72% { left:50%;}
    100% { top: 100px; left: 100%;}
  }
  ```
