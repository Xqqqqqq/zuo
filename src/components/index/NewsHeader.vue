<template>
  <div id="news-header">
    <!--导航栏-->
    <div id="header">

      <a href="" class="header1">
        <div class="header1-A">
          <span class="header1-a">ZUO</span>
          <span class="header1-b">HONEY WASABI</span>
        </div>
      </a>

      <div class="header2">
        <div class="header2-A">
          <ul class="header2-a">
            <a href="###"><li class="header2-a2" :style="color1" @click="click1">首页</li></a>
            <a href="###"><li class="header2-a3" :style="color2" @click="click2">深度</li></a>
            <a href="###"><li class="header2-a1" @click="click3">下载APP</li></a>
          </ul>
          <div class="header2-b">
            <input type="text" placeholder="输入关键字搜索" class="header2-b1">
            <a href=""><img src="../../common/img/fangda.png" alt="" class="fangda"></a>
          </div>
          <a href=""><img src="../../common/img/fangda.png" alt="" class="fangda1"></a>
        </div>
      </div>

      <div class="header3">
        <div class="header3-A">
          <a href=""><img src="../../common/img/user.png" alt="" class="user"></a>
          <a href="###"><span @click="opendeng">登录</span></a>
          <a href="###"><span @click="openzhu">注册</span></a>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
//  import axios from 'axios'
  export default {
    name: '',
    data(){
      return{
        color1:{
          color:'white'
        },
        color2:{
          color:'#9ea0a5'
        }
      }
    },
    methods:{
      click1:function () {
        this.$data.color1.color='white';
        this.$data.color2.color='#9ea0a5';
//        点击首页，打开导航栏下所有内容
        this.$emit('openzong');
      },
      click2:function () {
        this.$data.color2.color='white';
        this.$data.color1.color='#9ea0a5';
        this.$emit('openshendu');
      },
      click3:function () {
        this.$emit('openxiazai')
      },
      opendeng:function () {
        this.$emit('opendenglu');
      },
      openzhu:function () {
        this.$emit('openzhuce');
      }
    }
  }
</script>

<style scoped>
#header{
  height: 60px;
  width: 100%;
  background-color: #272c2f;
  padding-left: 30px;
  padding-right: 10px;
  overflow: hidden;
  box-sizing: border-box;
}
.header1-A{
  max-width: 182px;
}
  .header1{
    width: 25%;
    float: left;
    text-decoration: none;
    line-height: 60px;
    box-sizing: border-box;
  }
  .header2-A{
    width: 494px;
    margin: 0 auto;
  }
  .header2{
    width: 48%;
    float: left;
    box-sizing: border-box;
  }
  .header3{
    width: 27%;
    float: left;
  }
  .header1-a{
    font-size:20px;
    color: white;
    font-weight: bolder;
    margin-right: 5px;
  }
.header1-b{
  font-size:10px;
  color: rgba(255,255,255,.3);
  font-weight: bolder;
}
  .header2-a{
    list-style: none;
    font-size: 14px;
    float: left;
    line-height: 60px;
  }
  .header2-a2{
    color: white;
  }
  .header2-a a{
    text-decoration: none;
    color:#9ea0a5;
  }
  .header2-a li{
    float: left;
    margin-right: 30px;
  }
  .header2-b{
    position: relative;
    float: left;
  }
.header2-b1{
  width: 230px;
  height: 32px;
  border: none;
  border-radius: 4px;
  font-size: 14px;
  padding: 6px 30px 6px 10px;
  background-color: #464b4d;
  box-sizing: border-box;
  margin-top: 15px;
  outline:none;
  color:white;
}
.fangda{
  width: 20px;
  position: absolute;
  right:10px;
  top:20px;
}
.fangda1{
  display: none;
  width: 20px;
  padding-top: 20px;
}
.header3-A{
  float: right;
  padding-left: 20px;
  padding-top: 20px;
  font-size:14px;
  position: relative;
}
.user{
  position: absolute;
  left: -5px;
  top:18px;
  width: 22px;
}
.header3-A span{
  margin-right: 25px;
}
.header3-A a{
  text-decoration: none;
  color: #9ea0a5;
}


@media screen and (max-width:562px){
  .header2-b1{
    display: none;
  }
  .fangda1{
    display: block;
  }
}
  @media screen and (max-width: 890px){
    .header3-A span{
      display: none;
    }
    .header1-b{
      display: none;
    }
  }
  @media screen and (max-width: 720px){
    .header2-a1{
      display: none;
    }
  }

</style>
