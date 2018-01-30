<template>
  <div class="wrap">
    <div id="app">
      <pre id="code" ref="code">{{code}}</pre>
    </div>

    <div v-html="styleCode"></div>

    <div class="view">
      <div class="wrapper">
        <div class="lowerLip-wrapper">
          <div class="lowerLip"></div>
        </div>
        <div class="nose"></div>
        <div class="eye left"></div>
        <div class="eye right"></div>
        <div class="face left"></div>
        <div class="face right"></div>
        <div class="upperLip left"></div>
        <div class="upperLip right"></div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return {
      code: ``,
      finalCode:`
      /*

       *     hey，今天天气不错，一起用css画一个皮卡丘吧！
       *     首先reset一下默认样式

      */

    *{margin: 0; padding: 0; box-sizing: border-box;}
    *::after{
      box-sizing: border-box;
    }
    *::before{
      box-sizing: border-box;
    }

    /*
            好的，准备一个编辑区，一个预览区域，然后就可以愉快的开始画了~
    */

    .wrap{
      display: flex;
      flex-direction: column;
      height: 100vh;
    }
    #app{
      flex:1;
      height: 50%;
    }
    .view{
      flex:1;
      height: 50%;
    }

    /*
            白色太单调了，来个颜色吧
    */

    #code{
      overflow: auto;
      height: 100%;
      padding: 15px;
      background: #e2e2e2;
      color: #c13e3e;
    }

    /*
            来一个熟悉的黄皮肤
    */

    .view{
      height: 100%;
      border: 1px solid green;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #FEE433;
    }
    .wrapper{
      width: 100%;
      height: 165px;
      position: relative;
    }

    /*
            接着就是小鼻子了
    */

    .nose{
      width: 0px;
      height: 0px;
      border-style: solid;
      border-width: 12px;
      border-color: black transparent transparent;
      border-radius: 11px;
      position: absolute;
      left: 50%;
      top: 28px;
      margin-left: -12px;
    }

    /*
            继续，画两只眼睛
    */

    .eye{
      width: 49px;
      height: 49px;
      background: #2E2E2E;
      position: absolute;
      border-radius: 50%;
      border: 2px solid #000000;
    }

    /*
            当然，别忘了眼珠
    */

    .eye::before{
      content: '';
      display: block;
      width: 24px;
      height: 24px;
      background: white;
      position: absolute;
      border-radius: 50%;
      left: 6px;
      top:-1px;
      border: 2px solid #000;
    }

    /*
            调整一下眼睛的位置
    */

    .eye.left{
      right: 50%;
      margin-right: 90px;
    }
    .eye.right{
      left: 50%;
      margin-left: 90px;
    }

    /*
            接着是腮红
    */

    .face{
      width: 68px;
      height: 68px;
      background: #FC0D1C;
      border: 2px solid black;
      border-radius: 50%;
      position: absolute;
      top: 85px;
    }

    /*
            放好位置
    */

    .face.left{
      right: 50%;
      margin-right: 116px;
    }
    .face.right{
      left: 50%;
      margin-left: 116px;
    }

    /*
            OK  接下来画嘴唇
    */

    .upperLip{
      height: 25px;
      width: 80px;
      border: 2px solid black;
      position: absolute;
      top: 50px;
      background: #FDE348;
    }

    /*
            调整一下位置
    */

    .upperLip.left{
      right: 50%;
      border-bottom-left-radius: 40px 25px;
      border-top: none;
      border-right: none;
      transform: rotate(-20deg);
    }
    .upperLip.right{
      left: 50%;
      border-bottom-right-radius: 40px 25px;
      border-top: none;
      border-left: none;
      transform: rotate(20deg);
    }

    /*
            然后是舌头，画调皮一点叭！
    */

    .lowerLip-wrapper{
      bottom: 0;
      position: absolute;
      left: 50%;
      margin-left: -150px;
      height: 110px;
      overflow: hidden;
      width: 300px;
    }
    .lowerLip{
      height: 3500px;
      width: 300px;
      background: #990513;
      border-radius: 200px/2000px;
      border: 2px solid black;
      position: absolute;
      bottom: 0;
      overflow: hidden;
    }

    /*
            好的，画一下舌头的颜色
    */

    .lowerLip::after{
      content: '';
      position: absolute;
      bottom: -20px;
      width: 100px;
      height: 100px;
      background: #FC4A62;
      left: 50%;
      margin-left: -50px;
      border-radius: 50px;
    }

    /*
    
      噔噔噔，一只可爱的比卡丘就画好啦  送给你呀.
    
    */
      `
    }
  },
  created(){
    var n=0;
    var time = setInterval(()=>{
      this.code = this.finalCode.substring(0,n)
      n += 1
      code.scrollTop = 100000
      if(n >= this.finalCode.length){
        window.clearInterval(time);
      }
    },18)
  },
  computed:{
    styleCode(){
      return '<style>' + this.code + '</style>'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
