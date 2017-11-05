<template>
  <div id="news-deng-lu2" v-if="isShowDeng">
    <!--忘记密码部分-->
    <div class="wrap-A"></div>
    <div class="wrap">
      <div class="header">
        <div class="header-a">忘记密码</div>
      </div>
      <div class="content">
        <!--输入框-->
        <input type="text" class="content1" placeholder="手机号">
        <br>
        <input type="text" class="content1" placeholder="验证码">
        <br>
        <input type="password" class="content1" placeholder="新密码">
        <br>
        <input type="password" class="content1" placeholder="新密码确认">
        <br>
        <input type="button" class="footer" value="确认修改">
        <button class="content2">发送验证码</button>
      </div>
      <div class="cha" @click="closeDeng">
        <img src="../../assets/cha.png" alt="">
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: '',
      data(){
          return{
            isShowDeng:true
          }
      },
      methods:{
          closeDeng:function () {
            this.$emit('closedenglu2');
          }
      }
    }
</script>

<style scoped>
  .wrap-A {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(39, 44, 47, 0.9);
    z-index: 30;
  }
  .wrap {
    width: 540px;
    margin: 0 auto;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
  }
  .header {
    width: 100%;
    height: 82px;
    background-color: #272c2f;
    text-align: center;
    line-height: 82px;
    position: relative;
    font-size: 18px;
    color: #fff;
  }
  .content {
    width: 100%;
    background-color: white;
    padding: 50px 20px 20px 20px;
    box-sizing: border-box;
    position: relative;
  }
  .content1 {
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
    margin-bottom: 20px;
  }
  .footer {
    width: 100%;
    background-color: #1fd7e2;
    color: #fff;
    padding: 14px 20px;
    font-size: 18px;
    line-height: 22px;
    outline: none;
    border: none;
    margin-bottom: 20px;
    border-radius: 4px;
  }
  .content2{
    position: absolute;
    top: 123px;
    right: 26px;
    width: 115px;
    padding: 12px 18px;
    font-size: 14px;
    background-color: rgb(31, 215, 226);
    color: #fff;
    border-radius: 5px;
    outline: none;
    border: none;
  }
  .cha {
    width: 20px;
    position: absolute;
    right: -35px;
    top: 20px;
  }
</style>
