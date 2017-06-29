# vue
#### vue官网地址  http://cn.vuejs.org/v2/api/
#### vue gitHub地址  https://github.com/vuejs/vue

![](http://image.beekka.com/blog/2015/bg2015020110.png)
```
View 一般就是我们平常说的HTML文本的Js模板，里面可以嵌入一些js模板的代码，比如Mustache，比如jstl类似的模板伪代码

ViewModule 层里面就是我们对于这个视图区域的一切js可视业务逻辑，举个例子，比如图片走马灯特效，比如表单按钮点击提交，这些自定义事件的注册和处理逻辑都写在ViewModule里面了

Modul e就更简单了，就是对于纯数据的处理，比如增删改查，与后台CGI做交互
```



## 1. **简单入门**
  * **直接引入**

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
 * **相关指令**

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
   v-cloak   [v-clock]{display:none;}
   v-once

   ```

     重要常用：**v-if**、**v-show**、**v-if**、**v-for**、**v-model**、
---
 * **相关事件**
 ```
 eg1： 事件对象（$event）
  
   <div id="box">
        <input type="button" value="按钮" @click="show($event)">
   </div>
   
   <script>
      
    new Vue({
        el:'#box',
        data:{},
         methods:{
            show:function(ev){
                alert(ev.clientX);
            }
        }
    });
      
    </script>
    
 eg2：组织冒泡和默认行为

    <script src="vue.js"></script>
    <script>
        window.onload=function(){
            new Vue({
                el:'#box',
                data:{

                },
                methods:{
                    show:function(){
                        alert(1);
                    }
                }
            });
        };
    </script>
</head>
<body>
    <div id="box">
        <input type="button" value="按钮" @contextmenu.prevent="show()">
         <input type="button" value="按钮" @contextmenu.stop="show()">
    </div>
</body>

eg3:键盘事件
        Vue.config.keyCodes.ctrl=17;

        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                },
                methods:{
                    change(){
                        alert('改变了');
                    }
                }
            });
        };
    </script>
</head>
<body>
    <div id="box">
        <input type="text" @keyup.ctrl="change">
    </div>
</body>

 ```



 * **组件定义**
 ```
 eg1 
 
     <script>
        var Home={  //这是2.0组件
            template:'#aaa'
        };  //Vue.extend()


   <!--   Vue.component('my-aaa',Home);-->
        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                    msg:'welcome vue2.0'
                },
                components:{
                    'my-aaa':Home
                }
            });
        };
    </script>
 
 
    
eg2
     <script>
        Vue.component('my-aaa',{
            template:'#aaa'
        });

        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                    msg:'welcome vue2.0'
                }
            });
        };
    </script>


<body>
    <template id="aaa">
        <div>
            <h3>我是组件</h3>
            <strong>我是加粗标签</strong>
        </div>
    </template>
    <div id="box">
        <aaa></aaa>
        {{msg}}
    </div>
</body>
 
 
 
 
 
 ```


 * **组件之间通讯**
 ```
 1、父子组件之间的通讯
     <script>
        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                    a:'我是父组件数据'
                },
                components:{
                    'child-com':{
                        props:['msg'],
                        template:'#child',
                        methods:{
                            change(){
                                this.msg='被更改了'
                            }
                        }
                    }
                }
            });
        };
    </script>
</head>
<body>
    <template id="child">
        <div>
            <span>我是子组件</span>
            <input type="button" value="按钮" @click="change">
            <strong>{{msg}}</strong>
        </div>
    </template>

    <div id="box">
        父级: ->{{a}}
        <br>
        <child-com :msg="a"></child-com>
    </div>
        <script>
        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                    a:'我是父组件数据'
                },
                components:{
                    'child-com':{
                        props:['msg'],
                        template:'#child',
                        methods:{
                            change(){
                                this.msg='被更改了'
                            }
                        }
                    }
                }
            });
        };
    </script>
</body>


 1、单一组件之间的通讯
 
   <script>
        //准备一个空的实例对象
        var Event=new Vue();


        var A={
            template:`
                <div>
                    <span>我是A组件</span> -> {{a}}
                    <input type="button" value="把A数据给C" @click="send">
                </div>
            `,
            methods:{
                send(){
                    Event.$emit('a-msg',this.a);
                }
            },
            data(){
                return {
                    a:'我是a数据'
                }
            }
        };
        var B={
            template:`
                <div>
                    <span>我是B组件</span> -> {{a}}
                    <input type="button" value="把B数据给C" @click="send">
                </div>
            `,
            methods:{
                send(){
                    Event.$emit('b-msg',this.a);
                }
            },
            data(){
                return {
                    a:'我是b数据'
                }
            }
        };
        var C={
            template:`
                <div>
                    <h3>我是C组件</h3>
                    <span>接收过来的A的数据为: {{a}}</span>
                    <br>
                    <span>接收过来的B的数据为: {{b}}</span>
                </div>
            `,
            data(){
                return {
                    a:'',
                    b:''
                }
            },
            mounted(){
                //var _this=this;
                //接收A组件的数据
                Event.$on('a-msg',function(a){
                    this.a=a;
                }.bind(this));

                //接收B组件的数据
                Event.$on('b-msg',function(a){
                    this.b=a;
                }.bind(this));
            }
        };


        window.onload=function(){
            new Vue({
                el:'#box',
                components:{
                    'com-a':A,
                    'com-b':B,
                    'com-c':C
                }
            });
        };
    </script>
</head>
<body>
    <div id="box">
        <com-a></com-a>
        <com-b></com-b>
        <com-c></com-c>
    </div>
</body>


 ```
  * **生命周期**
  ![](http://cn.vuejs.org/images/lifecycle.png)


 * **前后台交互**
 1、vue-resouce（已经停止更新）  https://github.com/pagekit/vue-resource/tree/master
 2、**axios**（官方推荐）
     gitHub: https://github.com/mzabriskie/axios
     简书 http://www.jianshu.com/p/df464b26ae58  


 * **vue-router(路由)**
    github:  https://github.com/vuejs/vue-router

   简书   http://www.jianshu.com/p/cb918fe14dc6


 * **vue-cli**
 ```
 1、安装git（安装node送npm  有时候需要进行配置全局的环境变量）
 2、安装vue-cli  npm install vue-cli -g
 3、vue init simple demo
    vue init webpack-simple demo
    vue init webpack demo

 ```
 * **vuex**













