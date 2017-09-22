# activity10_1
canvas绘制红包雨活动（基于雪花飘落组件）

## 组件中源代码改动前的代码块

    if (settings.interaction == true) {
      canvas.addEventListener("click", function(e) {
          mX = e.clientX;
          mY = e.clientY;
      });
    }
    

## 在代码216 - 241 中新增了碰撞检测 以及一些逻辑的处理，改动后为

      var count = parseInt($(".js-point-count").html());
      canvas.addEventListener("click", function(e) {
          if(count <= 0) return alert('抽奖次数不足');
          var clientX = e.clientX;
          var clientY = e.clientY;
          for(var i=0;i < flakes.length;i++){
            //碰撞检测
            if(clientX > flakes[i].x && clientX < (flakes[i].x + flakes[i].size*2) && clientY > flakes[i].y && clientY < (flakes[i].y + flakes[i].size*2 ) ){
              count--;
              $(".js-point-count").html(count);
              $(".js-data-txt").html('恭喜您，抽中20000元红包大奖');
              $(".js-data-show-box").addClass('trans');
              flakeCount = 0;
              break;
            }
          }
          $('.js-btn-reverse').on(flag,function(){
            $(".js-data-show-box").removeClass('trans');
            setTimeout(function(){
              flakeCount = 10;
              $('.js-btn-reverse').unbind(flag);
            },300)
          })
          //mX = e.clientX;
          //mY = e.clientY;
      });
      
 ## 参数说明
 
    var defaults = {
      speed: 0, //速度
      interaction: true, //原组件为，是否悬浮雪花躲避功能，现为是否可以点击
      size: 2, // 尺寸
      count: 200, //数量
      opacity: 0, //透明度
      color: "#ffffff", //颜色
      windPower: 0, // 偏移量
      image: false //图片地址
    };
    
  ## 调用方法
  
    $("canvas.flare").let_it_snow({
      windPower: 0,
      speed: 0,
      color: "#392F52",
      size:40,
      opacity: 0.7,
      count: 10,
      interaction: false
    });
    
    可反复多次调用,如果觉得还可以，记得给个star哦
