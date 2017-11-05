<template>
  <div id="news-list-two" v-if="thisdata != null">
    <!--左侧全部页面-->
    <div class="wrap2">

      <div class="header">
        <!--全部，好，坏设计-->
        <div class="header1" @click="oquanbu">
          <img src="../../assets/jiugongge.png" alt="" class="header1-a">
          <div class="header1-b">全部</div>
          <img src="../../assets/xiajiantou.png" alt="" class="header1-c">
        </div>
        <div class="header2">
          <span>
            <img src="../../assets/duihaolan.png" alt="" class="header2-a" @click="click1">
            <img src="../../assets/duihaohui.png" alt="" class="header2-a header2-aa" v-show="isShow" @click="click3">
            <div class="header2-a1">好设计</div>
          </span>
          <span>
            <img src="../../assets/duihaohong.png" alt="" class="header2-b" @click="click2">
            <img src="../../assets/duihaohui.png" alt="" class="header2-b header2-bb" v-show="isSee" @click="click4">
            <div class="header2-b1">坏设计</div>
          </span>
        </div>
        <!--下拉菜单-->
        <div class="quanbu" v-if="quanbu">
          <div class="quanbu1"></div>
          <div class="div1">
            <img src="../../assets/jiugongge.png" alt="">
            <a href="###" class="quanbu2-b">全部</a>
          </div>
          <ul class="quanbu2" v-for="arr in arrs">
            <li class="quanbu22">
              <div :style="{backgroundColor:[arr.color]}" class="quanbu2-a"></div>
              <a href="###" class="quanbu2-b">{{arr['neirong']}}</a>
            </li>
          </ul>
        </div>

      </div>
      <div class="clear"></div>

      <div class="content" v-if="content">

        <div class="content1" v-for="(post,index) in thisdata['posts']">
          <!--每一小块，循环-->
          <div class="shang">
            <div class="shang-zuo">
              <img :src="post['owner']['avatar']" alt="" class="shang-zuo1">
              <div class="shang-zuo2" v-html="post['owner']['username']"></div>
            </div>

            <div class="shang-you">
              <img src="../../assets/yuanquan.png" alt="" class="shang-you1">
              <div class="shang-you2">{{post['likeCount']}}个赞同</div>
              <img src="../../assets/zhuanfa.png" alt="" class="shang-you3">
              <img src="../../assets/shenglue.png" alt="" class="shang-you4">
            </div>
          </div>
          <!--图中圆圈-->
          <div class="zhong">
            <img :src="post['postImage']['url']" alt="" class="zhong-A" @click="newslist2">
            <div class="zhong-AA"></div>
            <div class="zhong-BB" :style="{left:post['haloCenterRatio']['width_ratio']*100+'%',top:post['haloCenterRatio']['height_ratio']*100+'%'}"></div>
            <div class="zhong-B" :style="{left:post['haloCenterRatio']['width_ratio']*100+'%',top:post['haloCenterRatio']['height_ratio']*100+'%'}">
              <div class="zhong-B1">赞同</div>
              <div class="zhong-B2">这个态度</div>
            </div>
          </div>
          <!--文字部分-->
          <div class="xia">
            <div class="xia-A" v-html="post['postDescription']"></div>

            <div class="xia-B">
              <a href="" class="xia-B1">
                <img src="../../assets/landian.png" alt="" class="xia-B1-a">
                <span class="xia-B1-b" v-html="post['sceneTag']['name']"></span>
              </a>
              <a href="" class="xia-B1" v-for="tag in post['tags']">
                <img src="../../assets/heidian1.png" alt="" class="xia-B1-a">
                <span class="xia-B1-b" v-html="tag"></span>
              </a>
            </div>

            <!--<div class="xia-C-a">-->
            <div class="xia-C">
              <div class="xia-C1">
                <span class="xia-C1-b">{{post['commentedCount']}}条评论</span>
                <span class="xia-C1-c">更多评论...</span>
              </div>
              <!--this.$refs.ABC[index].childNodes[abc].childNodes[2].lastChild.-->
              <ul class="xia-C2" ref="ABC" >
                <li class="xia-C2-a" v-for="(comment,abc) in post['comments']" @mouseover="huifu1(abc,index)" @mouseout="huifu2(abc,index)">
                  <div class="xia-C2-aa">
                    <a href="" class="xia-C2-a1" v-html="comment['author']['username']"></a>
                    <span class="xia-C2-a2">-</span>
                    <span class="xia-C2-a3" v-html="comment['text']"></span>
                  </div>
                  <div class="xia-C2-ab" >
                    <span class="xia-C2-ab1" v-html="comment['timeAgo']"></span>
                    <img src="../../assets/deng.png" alt="" class="xia-C2-ab3">
                    <span class="xia-C2-ab2">点亮&nbsp;{{comment['likeNumber']}}</span>
                    <span class="xia-C2-ab4" ref="huifu" @click="zaiping(index,abc)">回复</span>
                  </div>
                </li>
              </ul>

              <textarea name="" class="xia-C3" placeholder="写下你的评论..." @click="pinglun(index)" ref="biaoqian"></textarea>
              <div class="xia-C4">
                <span class="xia-C41" ref="quxiao" @click="quxiao(index)">取消</span>
                <span class="xia-C42" ref="pinglun">评论</span>
              </div>

            </div>
            <!--</div>-->
            <!--<transition name="fade">-->
              <div class="dingwei" @mouseover="xiaoshou1" @mouseout="xiaoshou2" :style="left1">
                <div class="dingwei2">编辑推荐</div>
              </div>
            <!--</transition>-->

          </div>
        </div>

      </div>

    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: '',
    data() {
      return {
        thisdata:null,
        isShow: false,
        isSee: false,
        content:true,
        quanbu:false,
        left1:{
          left:-44 +'px'
        },
//        点击全部出现下拉菜单，小点和文字设置数组
        arrs:[
          {'color':'rgb(228, 204, 169)','neirong':'日用'},
          {'color':'rgb(161, 228, 64)','neirong':'公共'},
          {'color':'rgb(255, 71, 71)','neirong':'关爱'},
          {'color':'rgb(88, 0, 24)','neirong':'家居'},
          {'color':'rgb(174, 0, 255)','neirong':'时尚'},
          {'color':'rgb(255, 150, 0)','neirong':'美食'},
          {'color':'rgb(33, 140, 124)','neirong':'数码'},
          {'color':'rgb(255, 234, 0)','neirong':'视觉'},
          {'color':'rgb(0, 191, 243)','neirong':'空间'},
        ]
      }
    },
    mounted() {
      var that = this;
      axios.get('api/web_hot_posts').then(function (res) {
        that.thisdata = res.data;
      })
    },
    methods: {
      click1: function () {
        this.isShow = true;
        this.$emit('openhaosheji');
        this.content=false
      },
      click2: function () {
        this.isSee = true;
        this.$emit('openhuaisheji');
        this.content=false
      },
      click3: function () {
        this.isShow = false;
        this.content=true;
        this.$emit('closehaosheji')
      },
      click4: function () {
        this.isSee = false;
        this.content=true;
        this.$emit('closehuaisheji')
      },
      oquanbu:function () {
//        判断点击全部出现和消失
        if(this.quanbu ==false){
          this.quanbu=true;
        }else{
          this.quanbu=false;
        }
      },
//      使用js功能实现动画效果
      xiaoshou1:function () {
        this.left1.left='-100px'
      },
      xiaoshou2:function () {
        this.left1.left='-44px'
      },
      huifu1:function (abc,index) {
//        选择元素下的子元素节点：childNodes 最后一个子元素：lastChild
        this.$refs.ABC[index].childNodes[abc].childNodes[2].lastChild.style.display ='block'
      },
      huifu2:function (abc,index) {
        this.$refs.ABC[index].childNodes[abc].childNodes[2].lastChild.style.display ='none'
      },
      pinglun:function (ev) {
        this.$refs.quxiao[ev].style.display ='block';
        this.$refs.pinglun[ev].style.display ='block'
      },
      quxiao:function (ev) {
        this.$refs.quxiao[ev].style.display ='none';
        this.$refs.pinglun[ev].style.display ='none';
        this.$refs.biaoqian[ev].value =null;
      },
      zaiping:function (index,abc) {
        this.$refs.quxiao[abc].style.display ='block';
        this.$refs.pinglun[abc].style.display ='block';
        var that = this;
        axios.get('api/web_hot_posts').then(function (res) {
          that.thisdata = res.data;
        });
        this.$refs.biaoqian[index].value ='@'+that.thisdata.posts[index].comments[abc].author.username;
      },
      newslist2:function () {
        this.$emit('opennewslist2')
      }
    }
  }
</script>

<style scoped>
  #news-list-two {
    float: left;
  }

  .wrap2 {
    width: 540px;
  }

  .header {
    width: 100%;
    position: relative;
  }
  .clear{
    clear: both;
  }
  .quanbu{
    position: absolute;
    min-width: 100px;
    padding: 5px 10px;
    z-index: 99;
    left: -12px;
    top: 32px;
    border: 1px solid rgba(0,0,0,.15);
    border-radius: 4px;
    box-shadow: 0 6px 12px rgba(0,0,0,.175);
    background-color: white;
  }
  .quanbu2{
    border-top: 1px solid #ececec;
    padding:10px 0 0 0;
    font-size: 14px;
    list-style: none;
  }
  .quanbu22{
    overflow: hidden;
    padding: 5px 10px;
    text-align: center;
  }
  .quanbu22:hover{
    background-color: #cecece;
  }
  .quanbu2-a{
    width: 8px;
    height: 8px;
    float: left;
    margin-right:10px;
    border-radius: 50%;
  }
  .quanbu2-b{
    float: left;
    margin-top: -5px;
  }
  .quanbu2 a{
    text-decoration: none;
    color: #a6a7a7;
    font-weight: 500;
  }
  .quanbu1{
    position: absolute;
    width: 13px;
    height: 13px;
    border-left: 1px solid #ccc;
    border-top: 1px solid #ccc;
    background-color: #fff;
    transform: rotate(45deg);
    margin-left: -5px;
    top: -7px;
    left: 50%;
  }
  .div1{
    overflow: hidden;
    padding: 10px 15px;
  }
  .div1 img{
    width: 15px;
    float: left;
    margin-right: 5px;
    margin-left: -8px;
  }
  .div1 a{
    margin-top: -2px;
    text-decoration: none;
    color: #a6a7a7;
    font-weight: 500;
    font-size:14px;
  }
  .header1 {
    float: left;
  }

  .header1-a {
    width: 17px;
    float: left;
  }

  .header1-b {
    color: #272c2f;
    font-size: 16px;
    float: left;
    margin-left: 5px;
    margin-top: -2px;
  }

  .header1-c {
    width: 16px;
    margin-left: 5px;
  }

  .header2 {
    float: right;
    position: relative;
  }

  .header2 a {
    text-decoration: none;
    color: #959697;
    font-size: 14px;
  }

  .header2-a1 {
    margin-left: 5px;
    float: left;
    color: #959697;
    font-size: 14px;
  }

  .header2-b1 {
    margin-left: 5px;
    float: left;
    color: #959697;
    font-size: 14px;
  }

  .header2-a {
    width: 16px;
    float: left;
  }

  .header2-aa {
    position: absolute;
    left: -1px;
    top: -1px;
    width: 18px;
  }

  .header2-b {
    margin-left: 10px;
    width: 16px;
    float: left;
  }

  .header2-bb {
    position: absolute;
    left: 62px;
    top: -1px;
    width: 18px;
  }

  .content {
    width: 100%;
    margin-top: 20px;
  }

  .content1 {
    background-color: rgb(251,251,251);
    position: relative;
    margin-bottom: 30px;
    z-index: 20;
  }
  .content1:hover{
    box-shadow: 0 0 2px 2px rgb(230,230,230);
  }
  .dingwei {
    width: 103px;
    height: 30px;
    background-color: #1fd7e2;
    color: #fff;
    padding: 7px 10px 5px 45px;
    padding-bottom: 5px;
    font-size: 12px;
    background-image: url(../../assets/ok.png);
    background-repeat: no-repeat;
    background-position: 20px 5px;
    -webkit-background-size: 19px;
    background-size: 19px;
    border-radius: 4px 0 0 4px;
    position: absolute;
    left: -44px;
    top: 18px;
    z-index:-20;
    transition-property: left;
    transition-duration: 0.3s;
  }
  .shang {
    overflow: hidden;
    padding: 10px 15px 0px 15px;
    background-color: white;
  }

  .shang-zuo {
    float: left;
    height: 40px;
  }

  .shang-zuo1 {
    border-radius: 50%;
    width: 40px;
    float: left;
  }

  .shang-zuo2 {
    color: black;
    font-size: 14px;
    margin-top: 13px;
    float: left;
    margin-left: 8px;
  }

  .shang-you {
    float: right;
    padding-top: 13px;
  }

  .shang-you1 {
    width: 20px;
    float: left;
  }

  .shang-you2 {
    margin-left: 10px;
    font-size: 14px;
    color: #959697;
    float: left;
    margin-top: 2px;
  }

  .shang-you3 {
    width: 20px;
    margin-left: 15px;
  }

  .shang-you4 {
    width: 20px;
    margin-left: 15px;
  }

  .zhong {
    margin-top: 10px;
    position: relative;
  }
  .zhong-AA{
    position: absolute;
    top: 0;
    left: 0;
    width: 540px;
    height: 540px;
    background-color: rgba(45,47,49,0.2);
    display: none;
  }
  .zhong:hover .zhong-AA{
    display: block;
    transition: all 1s;
  }
  .zhong:hover .zhong-B1{
    display: block;
    transition: all 1s;
  }
  .zhong:hover .zhong-B2{
    display: block;
    transition: all 1s;
  }
  .zhong-B {
    border: 1px solid #1fd7e2;
    background-color: rgba(31, 217, 255, 0.2);
    width: 110px;
    height: 110px;
    border-radius: 50%;
    text-align: center;
    padding: 25px;
    position: absolute;
    margin-top: -55px;
    margin-left: -55px;
  }

  @-webkit-keyframes move1 {
    0% {
      transform: scale(1);
      opacity: 1;
    }
    100% {
      transform: scale(1.5);
      opacity: 0;
    }
  }

  .zhong-BB {
    border: 1px solid #1fd7e2;
    width: 110px;
    height: 110px;
    border-radius: 50%;
    animation: move1 1s linear infinite;
    position: absolute;
    top: 0;
    left: 0;
    margin-top: -55px;
    margin-left: -55px;
  }

  .zhong-B1 {
    font-size: 24px;
    font-weight: 500;
    color: white;
    display: none;
  }

  .zhong-B2 {
    font-size: 14px;
    color: white;
    display: none;
  }

  .xia {
    padding: 20px 25px 18px;
  }

  .xia-A {
    font-size: 14px;
    color: #595c5d;
  }

  .xia-B {
    margin-top: 25px;
    border-bottom: 1px solid rgb(231, 231, 231);
    padding-bottom: 20px;
  }

  .xia-B1 {
    text-decoration: none;
    margin-right: 10px;
  }

  .xia-B1-a {
    width: 10px;
  }

  .xia-B1-b {
    color: #a6a7a7;
    font-size: 14px;
  }

  .xia-C {
    margin-top: 20px;
  }

  .xia-C1 {
    margin-bottom: 15px;
    background-image: url(../../assets/duihua.png);
    background-repeat: no-repeat;
    -webkit-background-size: 15px;
    background-size: 15px;
    background-position: 0 5px;
    padding-left: 13px;
  }

  .xia-C1-b {
    color: #a6a7a7;
    margin-left: 8px;
    margin-right: 10px;
    font-size: 14px;
  }

  .xia-C1-c {
    color: #a6a7a7;
    font-size: 14px;
  }

  .xia-C2 {
    list-style: none;
    padding: 0;
    border-bottom: 1px solid rgb(231, 231, 231);
  }

  .xia-C2-a {
    margin-bottom: 15px;
  }
  .xia-C2-a:hover{
    background-color: rgb(244,244,244);
  }

  .xia-C2-a1 {
    color: black;
    font-size: 12px;
    text-decoration: none;
  }

  /*li:hover{*/
    /*background-color: red;*/
  /*}*/

  .xia-C2-a3 {
    color: #a6a7a7;
    font-size: 12px;
  }

  .xia-C2-ab {
    overflow: hidden;
    margin-top: 5px;
  }

  .xia-C2-ab1 {
    float: left;
    color: #c9c9c9;
    font-size: 12px;
  }

  .xia-C2-ab2 {
    float: right;
    color: #a1a2a3;
    font-size: 12px;
  }

  .xia-C2-ab3 {
    float: right;
    width: 15px;
    margin-left: 5px;
  }
  .xia-C2-ab4 {
    float: right;
    color: #a1a2a3;
    font-size: 12px;
    margin-right: 15px;
    display: none;
  }

  .xia-C3 {
    width: 100%;
    border: none;
    outline: none;
    font-size: 14px;
  }
  .xia-C4{
    overflow: hidden;
  }
  .xia-C4 span{
    font-size:14px;
  }
  .xia-C41{
    float: left;
    display: none;
  }
  .xia-C42{
    float: right;
    display: none;
  }
</style>
