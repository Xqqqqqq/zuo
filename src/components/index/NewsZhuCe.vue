<template>
  <div class="news-zhu-ce" v-if="isShowZhu">
    <!--注册页面-->
    <div class="wrap-A" @click="closeZhu"></div>
    <div class="wrap">

      <div class="header">
        <img src="../../assets/bird1.png" alt="" class="header1">
        <div class="header2">欢迎回到 ZUO</div>
      </div>

      <div class="content">

        <div class="content1">
          <div class="content1-a">
            <img src="../../assets/weibo1.png" alt="" class="img1">
            <img src="../../assets/weixin.png" alt="" class="img2">
          </div>
          <div class="content1-b">你可以使用第三方社交账号直接登录</div>
          <div class="content1-c">
            <div class="content1-c1"></div>
            <div class="content1-c2">或者</div>
            <div class="content1-c3"></div>
          </div>
        </div>

        <div class="content2">
          <input type="text" class="content2-a" placeholder="手机号">
          <br>
          <input type="text" class="content2-b" placeholder="验证码">
          <input class="content2-c" value="发送验证码" type="button">
          <br>
          <input type="password" class="content2-d" placeholder="密码">
          <br>
          <input type="password" class="content2-e" placeholder="确认密码">
        </div>

        <div class="content3">
          <div class="content3-a">
            <img src="../../assets/danxuan1.png" alt="" class="content3-a1">
            <div class="content3-a2">我已经认真阅读并同意ZUO的</div>
            <a href="" class="content3-a3">《用户协议》</a>
          </div>
          <a href="###" class="content3-b" @click="odenglu">已有账号，登录</a>
        </div>

        <button class="content4">注册帐号</button>
        <div class="cha" @click="closeZhu">
          <img src="../../assets/cha.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: '',
      data(){
          return{
            isShowZhu:true
          }
      },
      methods:{
        closeZhu:function () {
          this.isShowZhu = false;
          this.$emit('closezhuce')
        },
        odenglu:function () {
          this.$emit('opendenglu');
          this.$emit('closezhuce');
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

  a {
    text-decoration: none;
  }

  .wrap {
    /*position: relative;*/
    width: 540px;
    margin: 0 auto;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
  }

  .cha {
    width: 20px;
    position: absolute;
    right: -30px;
    top: 15px;
  }

  .header {
    width: 100%;
    height: 82px;
    background-color: #272c2f;
    text-align: center;
    line-height: 82px;
    position: relative;
  }

  .header1 {
    width: 28px;
    border-radius: 50%;
    position: absolute;
    left: 172px;
    top: 27px;
  }

  .header2 {
    font-size: 18px;
    color: white;
  }

  .content {
    width: 100%;
    background-color: white;
    padding: 20px;
    box-sizing: border-box;
  }

  .content1 {
    margin-top: 20px;
    text-align: center;
  }

  .img1 {
    width: 32px;
    margin-right: 30px;
  }

  .img2 {
    width: 33px;
  }

  .content1-b {
    font-size: 14px;
    color: #a6a7a7;
    margin-top: 20px;
  }

  .content1-c {
    width: 100%;
    overflow: hidden;
    margin-top: 20px;
    box-sizing: border-box;
    margin-left: 84px;
  }

  .content1-c1 {
    height: 1px;
    width: 138px;
    background-color: #d7d8d8;
    float: left;
    margin-top: 10px;
  }

  .content1-c2 {
    float: left;
    color: #d7d8d8;
    margin-left: 10px;
    margin-right: 10px;
  }

  .content1-c3 {
    height: 1px;
    width: 138px;
    background-color: #d7d8d8;
    float: left;
    margin-top: 10px;
  }

  .content2 {
    position: relative;
    margin-top: 20px;
  }

  .content2-a {
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
    margin-bottom: 20px;
  }

  .content2-b {
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
    margin-bottom: 20px;
  }
  .content2-c {
    position: absolute;
    right: 0;
    bottom: 4px;
    width: 115px;
    padding: 12px 18px;
    font-size: 14px;
    background-color: rgb(31, 215, 226);
    color: #fff;
    border-radius: 5px;
    outline: none;
    border: none;
  }
  .content2-d{
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
    margin-bottom: 20px;
  }
  .content2-e{
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
  }
  .content3 {
    margin-top: 20px;
    overflow: hidden;
  }
  .content3-a{
    float: left;
  }
  .content3-a1{
    width: 25px;
    float: left;
  }
  .content3-a2{
    float: left;
    margin-top: 3px;
    margin-left: 3px;
    font-size:14px;
    font-weight: bold;
  }
  .content3-a3{
    font-size:14px;
    color: #1fd7e2;
  }
  .content3-b{
    float: right;
    font-size: 14px;
    color: black;
  }
  .content4 {
    font-size: 18px;
    background-color: #1fd7e2;
    color: #fff;
    width: 100%;
    height: 50px;
    text-align: center;
    cursor: pointer;
    margin-top: 20px;
    border: none;
    outline: none;
  }
</style>
