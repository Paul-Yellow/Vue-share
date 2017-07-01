<!DOCTYPE html>
<html>
<head>
  <title>Welcome to Vue</title>

  <meta http-equiv="content-type" content="text/html;charset=utf-8">
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
  <script src="bower_components/vue-resource/dist/vue-resource.js"></script>
  <style>
    .gray {
      background: #ccc;
    }

  </style>
</head>
<body>
    <div id="box">
        <span v-red>
            asdfasd
        </span>
        <span v-red>
            asdfasd
        </span>
        <span v-red>
            asdfasd
        </span>
    </div>
    <script>
        Vue.directive('red',function(){
            this.el.style.background='red';
        });

        window.onload=function(){
            var vm=new Vue({
                el:'#box',
                data:{
                    msg:'welcome'
                }
            });
        };

    </script>

</body>
</html>

