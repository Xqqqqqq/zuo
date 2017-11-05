<template>
  <div id="news-deng-lu" v-if="isShowDeng">
    <!--登录-->
    <div class="wrap-A" @click="closeDeng"></div>
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
        <!--输入框内容-->
        <div class="content2">
          <input type="text" class="content2-a" placeholder="手机号" v-model="value">
          <span class="a1" v-if="see">
              <span class="a1-a"></span>
              <span class="a1-b">请填写手机号码</span>
          </span>
          <span class="a2" v-if="see1">
              <span class="a2-a"></span>
              <span class="a2-b">手机号码格式不正确</span>
          </span>
          <br>
          <input type="text" class="content2-b" placeholder="验证码" v-if="CanSee">
          <input class="content2-c" value="发送验证码" type="button" v-if="CanSee">
          <input class="content2-b content2-d" placeholder="密码" type="password" v-if="CanWatch">
        </div>
        <!--手机密码与手机验证码登录切换-->
        <div class="qiehuan">
          <div class="content3" v-if="CanSee">
            <a href="###" class="content3-a" @click="ozhuce">没有账号？去注册</a>
            <a href="###" class="content3-b">
              <img src="../../assets/suo.png" alt="" class="content3-b1">
              <div class="content3-b2" @click="NotSee">手机密码登录</div>
            </a>
          </div>
          <div class="content3 content33" v-if="CanWatch">
            <a href="###" class="content3-a" @click="openWang">忘记密码？</a>
            <a href="###" class="content3-b">
              <img src="../../assets/phone.png" alt="" class="content3-b1">
              <div class="content3-b2" @click="NotWatch">手机验证码登录</div>
            </a>
          </div>
        </div>

        <button class="content4" @click="denglu" :style="border">登录</button>
        <div class="cha" @click="closeDeng">
          <img src="../../assets/cha.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: '',
    data() {
      return {
        isShowDeng: true,
        CanSee:true,
        CanWatch:false,
        see:false,
        see1:false,
        value:'',
        border:{
          border:'none'
        }
      }
    },
    methods: {
      closeDeng: function () {
        this.isShowDeng = false;
        this.$emit('closedenglu')
      },
      ozhuce: function () {
        this.$emit('openzhuce');
        this.$emit('closedenglu');
      },
      NotSee:function () {
        this.CanSee=false;
        this.CanWatch=true
      },
      NotWatch:function () {
        this.CanWatch=false;
        this.CanSee=true;
      },
      openWang:function () {
        this.$emit('openwangji');
        this.$emit('closedenglu')
      },
//      判断是否有手机号和手机号正误
      denglu:function () {
        if(this.value ==''){
          this.see =true;
        }
        if(this.value !='' && !(/^1[34578]\d{9}$/)){
          this.see1 =true;
          this.$data.border.border ='1px solid #f94815';
        }
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
  .a1,.a2{
    position: absolute;
    left: 100%;
    top: 10px;
    margin-left: 10px;
    background-color: #f94815;
    color: #fff;
    border-radius: 4px;
    line-height: 30px;
    min-width: 225px;
    text-align: center;
    height: 30px;
  }
  .a1-a,.a2-a{
    border-top: 10px solid transparent;
    border-bottom: 10px solid transparent;
    border-right: 10px solid #f94815;
    position: absolute;
    top: 6px;
    left: -6px;
    width: 0;
    height: 0;
  }
  .a1-b,.a2-b{
    font-size: 14px;
  }
  .content2-b {
    width: 100%;
    background-color: #f7f7f7;
    padding: 14px 20px;
    font-size: 14px;
    line-height: 22px;
    outline: none;
    border: none;
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

  .content2-d {
    position: absolute;
    left: 0;
    top: 68px;
  }
  .content3 {
    margin-top: 20px;
    overflow: hidden;
  }
  .content33{
    margin-top: 65px;
  }
  .content3-a {
    color: #a6a7a7;
    font-size: 14px;
    float: left;
  }

  .content3-b {
    float: right;
  }

  .content3-b1 {
    width: 20px;
    float: left;
  }

  .content3-b2 {
    float: left;
    color: #272c2f;
    font-size: 14px;
    margin-top: 2px;
    margin-left: 4px;
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
