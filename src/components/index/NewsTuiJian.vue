<template>
  <div id="news-tui-jian" v-if="thisdata != null">
    <!--推荐关注部分-->
    <div class="header">推荐关注</div>

    <div class="content">

      <div class="content1" v-for="(reco_user,index) in thisdata['reco_users']">
        <div class="content1-zuo">
          <div class="zuo1" v-html="reco_user['username']"></div>
          <div class="zuo2">
            <a href="" v-html="reco_user['introduction']"></a>
          </div>
        </div>
        <div class="content1-you">
          <img :src="reco_user['avatar']" alt="" id="you1" >
          <div id="you2" :style="opacity" ref="mask" @mouseenter="mouseoverMask(index)"  @mouseleave="mouseoutMask(index)"></div>
        </div>
      </div>
    </div>

    <div class="footer">

      <div class="footer-a" @mouseover="mouseover1" @mouseout="mouseout1">
        <div class="zuo-a">
          <a href="">下载iOS版 App</a>
        </div>
        <div class="you-a">
          <img src="../../assets/bird1.png" alt="">
          <img src="../../assets/bird2.png" alt="" class="img2" v-if="isShow">
        </div>
      </div>

      <div class="footer-a" @mouseover="mouseover2" @mouseout="mouseout2">
        <div class="zuo-a">
          <a href="">关注微信公众号</a>
        </div>
        <div class="you-a">
          <img src="../../assets/erweima1.png" alt="">
          <img src="../../assets/erweima2.png" alt="" class="img4" v-if="isSee">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
    export default {
        name: '',
      data(){
          return{
            thisdata:null,
            isShow:false,
            isSee:false,
            color3:{
              color:'#535557'
            },
            color4:{
              color:'#999a9a'
            },
            opacity:{
              opacity:'0'
            }

          }
      },
      mounted(){
        var that =this;
        axios.get('api/web_reco_users').then(function (res) {
          that.thisdata =res.data;
        })
      },
      methods:{
        mouseover1:function () {
          this.isShow=true;
        },
        mouseover2:function () {
          this.isSee=true;
        },
        mouseout1:function () {
          this.isShow=false;
        },
        mouseout2:function () {
          this.isSee=false;
        },
        mouseoverMask:function (ev) {
          this.$refs.mask[ev].style.opacity="0.5";
        },
        mouseoutMask:function (ev) {
          this.$refs.mask[ev].style.opacity="0";
        }
      }
    }
</script>

<style scoped>
  #news-tui-jian{
    float:right;
    width: 220px;
    margin-left: 30px;
    margin-top: 40px;
  }
  a{
    text-decoration: none;
  }
  .header{
    font-size: 14px;
    font-weight: 500;
    color: #272c2f;
  }
  .content{
    margin-top: 15px;
  }
  .content1{
    border-bottom: 1px solid rgb(231,231,231);
    overflow: hidden;
    padding-bottom: 10px;
    padding-top: 10px;
  }
  .content1-zuo{
    width: 146px;
    float: left;
  }
  .zuo1{
    color: #535557;
    font-size:14px;
    font-weight: 500;
    margin-bottom: 5px;
  }
  .zuo1:hover{
    color:#999a9a;
  }
  .zuo2{
    line-height: 18px;
  }
  .zuo2 a{
    color: #999a9a;
    font-size: 12px;
  }
  .zuo2 a:hover{
    color: #535557;
  }
  .content1-you{
    float: right;
    position: relative;
  }
  #you1{
    width: 40px;
    border-radius: 5px;
  }
  #you2{
    width: 40px;
    height: 40px;
    background-color:rgb(46,48,50);
    border-radius: 5px;
    position: absolute;
    left: 0;
    top: 0;
  }
  .footer{
    margin-top: 30px;
  }
  .footer-a{
    overflow: hidden;
    border: 1px solid #ececec;
    margin-bottom: 10px;
  }
  .zuo-a{
    float: left;
    width: 169px;
    height: 50px;
    border-right: 1px solid #ececec;
    text-align: center;
    line-height: 50px;
  }
  .zuo-a a{
    color: #272c2f;
    text-decoration: none;
    font-size:14px;
  }
  .you-a{
    height: 50px;
    text-align: center;
    padding: 13px 0 10px 6px;
    position: relative;
  }
  .footer-a img{
    width: 25px;
    margin: 0 auto;
    line-height: 50px;
  }
  .img2{
    position: absolute;
    right: 12px;
    bottom:13px;
  }
  .img4{
    position: absolute;
    right: 12px;
    bottom:13px;
  }
</style>
