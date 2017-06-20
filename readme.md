# vue
#### vue官网地址  http://cn.vuejs.org/v2/api/
#### vue gitHub地址  https://github.com/vuejs/vue



## 1. 简单入门
  * 直接引入
  ``` javascript
 <script src="https://unpkg.com/vue/dist/vue.js"></script>


 new Vue({
        el: '#app',               //挂载的元素
        data: {                   //代理数据
            msg: '让健康更简单'
        },
        methods: {                   //自定义的方法
            change: function () {
                this.msg = '泓华是个大家庭'
                console.log(this)
            }


        }
    })

      除了这些还有很多 例如：computetd（属性计算） 、filter（自定义过滤器）、还有生命周期中的钩子函数
  ```
------
 * 相关指令

   1 、双向数据绑定
   ``` javascript
   /*--------html部分---------*/
    <div id="app">
    <input type="text" v-model="msg">
    <hr>
    {{msg}}
    <hr>
    <input type="button" v-on:click="change" value="点我">

    </div>
    /*--------js 部分---------*/
    <script>
    new Vue({
        el: '#app',
        data: {
            msg: '让健康更简单'
        }

    })
   </script>
   v-text    更新元素的内容（只是文本节点text） {{msg}}
   v-html   更新元素的 innerHTML(官网不推荐使用)
   v-show    用于根据条件展示元素的选项
   v-if      （同上 但是两者之间会有去别）
   v-else     组合v-if 使用
   v-else-if    同上
   v-for       进行列表渲染
   v-on        绑定事件使用  可缩写为 @click
   v-bind      绑定属性 可缩写为 :class
   v-model     多用于表单元素  双向数据的一个绑定
   v-pre
   v-cloak
   v-once

   还有三个属性  slot key  ref
   ```

     重要常用：**v-if**、**v-show**、**v-if**、**v-for**、**v-model**、
---
 * 相关事件
 ```






 ```



 * 组件定义


 * 组件之间通讯


 * 前后台交互


 * vue-cli













