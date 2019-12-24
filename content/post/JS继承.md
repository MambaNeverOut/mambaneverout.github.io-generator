---
title: "JS继承"
date: 2019-12-10T10:04:19+08:00
draft: false
---

# JS 实现继承有两种通用的方式

1. 构造函数 + 原型

   - 不写 Parent.call(this, name1)
     ![注释Parent.call(this, name1)](/images/nocall.png)
     注释掉 Parent.call(this, name1)之后，执行 pMethod 函数，pMethod 函数被 child 调用，this 指向 child，但在 child 中无法找到 name1，所以输出 undefined。

   - 正确代码
     ![正确代码](/images/normal.jpg)
     正确代码，需要把 this 指向通过 new Child 构造出来的实例对象(child)，并且把参数 name1 传给 Parent。

   * 终极代码

     ```
      function Parent(name1){
          this.name1 = name1
      }
      Parent.prototype.pMethod = function(){
          console.log(this.name1)
      }

      function Child(name2, name1){
          Parent.call(this, name1) // 得分点
          this.name2 = name2
      }
      Child.prototype.__proto__ = Parent.prototype
          //上面这句代码的古板写法应该是下面三句
          //const empty = function(){}
          //empty.prototype = Parent.prototype
          //Child.prototype = new empty()
          //还有一句也很重要，只是被人们忽视了
          //Child.prototype.constructor = Child

      Child.prototype.cMethod = function(){
          console.log(this.name2)
      }
     ```

2. class
   ```
   class Parent{
       constructor(name1){
           this.name1 = name1
       }
       pMethod(){
           console.log(this.name1)
       }
   }
   class Child extends Parent{
       constructor(name2, name1){
           super(name1) // 重点
           this.name2 = name2
       }
       cMethod(){
           console.log(this.name2)
       }
   }
   ```
   构造函数中使用的 super() 只能在构造函数中使用，并且必须在使用 this 关键字前调用。不调用的话执行函数会报错。
   ![](/images/class-error.jpg)
