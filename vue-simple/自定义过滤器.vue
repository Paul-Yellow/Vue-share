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
        {{msg | toDou('12','5')}}
    </div>

        <script>
        Vue.filter('toDou',function(n,a,b){
            alert(a+','+b);
            //alert(input);
            return n<10?'0'+n:''+n;
        });

        window.onload=function(){
            new Vue({
                el:'#box',
                data:{
                    msg:9
                }
            });
        };
    </script>
</body>
</html>
