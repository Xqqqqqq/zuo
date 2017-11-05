<template>
  <div class="news-list-two2" v-if="thisdata !=null">
    <!--点击全部标签下的二级页面-->
    <div class="wrap-A" @click="closelist2"></div>
    <div class="wrap">
      <div class="zuo">
        <div class="zuo-header">
          <div class="zuo-header-A">
            <img :src="thisdata['post']['owner']['avatar']" alt="" class="zuo-header-A-a">
            <div class="zuo-header-A-b">{{thisdata['post']['owner']['username']}}</div>
            <div class="zuo-header-A-c">发布于{{thisdata['post']['timeAgo']}}</div>
          </div>

          <div class="zuo-header-B">
            <img src="../../assets/zhuanfa.png" alt="" class="zuo-header-B-a">
            <img src="../../assets/shenglue.png" alt="" class="zuo-header-B-b">
          </div>
        </div>

        <div class="zuo-content">
          <img :src="thisdata['post']['postImage']['url']" alt="">
          <div class="yuan" :style="{left:thisdata['post']['haloCenterRatio']['width_ratio']*100+'px',top:thisdata['post']['haloCenterRatio']['height_ratio']*100+'px'}">
            <div class="yuan-a">赞同</div>
            <div class="yuan-b">这个态度</div>
          </div>
          <div class="yuan2" :style="{left:thisdata['post']['haloCenterRatio']['width_ratio']*100+'px',top:thisdata['post']['haloCenterRatio']['height_ratio']*100+'px'}"></div>
          <div class="zuo-content-A"></div>
         </div>
      </div>

      <div class="you">

        <div class="you-header">
          <div class="you-header-a">
            <div class="header-zuo">
              <img src="../../assets/heiyuan.png" alt="">
              <div>赞同这个态度</div>
            </div>
            <div class="header-you">{{thisdata['post']['likeCount']}}个赞同</div>
          </div>

          <div class="you-header-b">
            <div class="header-b1"></div>
            <div class="header-b2">
              <img v-for="like in thisdata['post']['likes']" :src="like['avatar']" alt="" class="header-b3">
              <!--<img src="../../assets/bird2.png" alt="" class="header-b4">-->
            </div>
          </div>
        </div>

        <div class="you-content">
          <div class="you-content1">
            <div class="content1-1">{{thisdata['post']['postDescription']}}</div>
            <div class="content1-2">
              <img src="../../assets/landian.png" alt="">
              <span class="content1-22">{{thisdata['post']['sceneTag']['name']}}</span>
              <a href="###" class="content1-23" v-for="tag in thisdata['post']['tags']">
                <img src="../../assets/heidian1.png" alt="">
                <span>{{tag}}</span>
              </a>
            </div>
          </div>

          <div class="you-content2">
            <div class="content2-1">
              <img src="../../assets/duihua.png" alt="">
              <span>{{thisdata['post']['commentedCount']}}条评论</span>
            </div>

            <div class="content2-2" v-for="comment in thisdata['post']['comments']">
              <div class="content2-2A">
                <a href="###" class="content2-2a">{{comment['author']['username']}} -</a>
                <span class="content2-2b">{{comment['text']}}</span>
              </div>

              <div class="content2-2B">
                <span class="content2-2a1" v-html="comment['timeAgo']"></span>
                <img src="../../assets/deng.png" alt="" class="content2-2a2">
                <span class="content2-2a3">点亮&nbsp;{{comment['likeNumber']}}</span>
                <span class="content2-2a4">回复</span>
              </div>
            </div>
          </div>
        </div>

        <div class="you-footer">
          <textarea name="" class="you-footer1" placeholder="写下你的评论..."></textarea>
          <div class="you-footer2">
            <span class="you-footer2a">取消</span>
            <span class="you-footer2b">评论</span>
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
      data(){
          return{
            thisdata:null,
          }
      },
      mounted(){
        var that =this;
        axios.get('api/post/58a159ce128fe1006cf3cc8d').then(function (res) {
          that.thisdata =res.data;
        })
      },
      methods:{
        closelist2:function () {
          this.thisdata=null;
          this.$emit('closelist2')
        }
      }
    }
</script>

<style scoped>
  a{
    text-decoration: none;
  }
  .wrap-A {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(39, 44, 47, 0.9);
    z-index: 99;
  }
  .wrap{
    width: 850px;
    height: 620px;
    box-sizing: border-box;
    margin: 0 auto;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
    background-color: white;
    display: -webkit-inline-flex;
    justify-content: space-between;
    padding: 20px;
    overflow: hidden;
  }
  .zuo{
    width: 540px;
    float: left;
    box-sizing: border-box;
  }
  .zuo-header{
    width: 100%;
    overflow: hidden;
  }
  .zuo-content{
    width: 100%;
  }
  .you{
    width: 250px;
    float: right;
    box-sizing: border-box;
  }
  .zuo-header-A{
    overflow: hidden;
    float: left;
  }
  .zuo-header-A-a{
    float: left;
    width: 40px;
    border-radius: 50%;
    margin-right: 10px;
  }
  .zuo-header-A-b{
    float: left;
    font-size: 14px;
    font-weight: 500;
    color: #272c2f;
    cursor: pointer;
    margin-top: 10px;
  }
  .zuo-header-A-c{
    float: left;
    padding-left: 10px;
    color: #a6a7a7;
    font-size: 14px;
    margin-top: 11px;
  }
  .zuo-header-B{
    float: right;
  }
  .zuo-header-B img{
    width: 20px;
    margin-left: 15px;
    margin-top: 10px;
  }
  .zuo-content{
    position: relative;
  }
  .zuo-content:hover .zuo-content-A{
    display: block;
    transition: all 0.3s;
  }
  .zuo-content:hover .yuan-a{
    display: block;
    transition: all 0.3s;
  }
  .zuo-content:hover .yuan-b{
    display: block;
    transition: all 0.3s;
  }
  .zuo-content-A{
    position: absolute;
    top: 10px;
    left: 0;
    width: 540px;
    height: 540px;
    background-color: rgba(45,47,49,0.2);
    display: none;
    /*鼠标移入变放大镜*/
    cursor: zoom-in;
  }
  .zuo-content img{
    margin-top: 10px;
  }
  .yuan{
    position: absolute;
    border: 1px solid #1fd7e2;
    background-color: rgba(31,217,255,0.2);
    border-radius: 50%;
    width: 110px;
    height: 110px;
    text-align: center;
    padding:25px;
    margin-top: 110px;
    margin-left: 165px;
  }
  .yuan-a{
    font-size: 24px;
    font-weight: 500;
    color: white;
    display: none;
  }
  .yuan-b{
    font-size: 14px;
    color: white;
    display: none;
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
  .yuan2{
    position: absolute;
    top: 0;
    left: 0;
    border: 1px solid #1fd7e2;
    border-radius: 50%;
    width: 110px;
    height: 110px;
    animation: move1 1s linear infinite;
    margin-top: 110px;
    margin-left: 165px;
  }
  .you-header-a{
    overflow: hidden;
  }
  .header-zuo{
    float: left;
    margin-top: 10px;
  }
  .header-zuo img{
    width: 20px;
    float: left;
  }
  .header-zuo div{
    float: left;
    color: #a6a7a7;
    padding-left: 5px;
    font-size:15px;
  }
  .header-you{
    float: right;
    color: #a6a7a7;
    font-size:15px;
    margin-top: 10px;
  }
  .you-header-b{
    width: 100%;
    position: relative;
    padding: 10px;
    border-radius: 4px;
    background-color: #eaeced;
    height: 60px;
    margin-top: 15px;
  }
  .header-b1{
    position: absolute;
    right: 15px;
    top: -6px;
    width: 13px;
    height: 13px;
    border-left: 1px solid #eaeced;
    border-top: 1px solid #eaeced;
    background-color: #eaeced;
    transform: rotate(45deg);

  }
  .header-b3{
    width: 40px;
    border-radius: 50%;
    cursor: pointer;
    margin-right: 10px;
  }
  .you-content1{
    padding: 15px;
  }
  /*给页面加滚动条*/
  .you-content{
    max-height: 420px;
    overflow-y: auto;
    overflow-x: hidden;
  }
  .content1-1{
    padding: 13px 0;
    border-top: 1px solid #ececec;
    font-size:13px;
    color: #595c5d;
    line-height: 22px;
  }
  .content1-2{
    line-height: 30px;
    padding-bottom: 10px;
    border-bottom: 1px solid #ececec;
  }
  .content1-2 img{
    width: 8px;
  }
  .content1-2 span{
    color: #a6a7a7;
    font-size:14px;
  }
  .content1-22{
    margin-right: 10px;
  }
  .content1-23{
    margin-right: 75px;
  }
  .content2-1{
    margin-bottom: 25px;
  }
  .content2-1 img{
    width: 18px;
  }
  .content2-2{
    margin-bottom: 10px;
  }
  .content2-2a{
    font-size: 12px;
    font-weight: 600;
    color: #272c2f;
  }
  .content2-2b{
    font-size: 12px;
    color: #595c5d;
    margin-left: 5px;
  }
  .content2-2B{
    overflow: hidden;
    margin-top: 5px;
  }
  .content2-2:hover .content2-2a4{
    display: block;
  }
  .content2-2a1{
    float: left;
    color: #c9c9c9;
    font-size: 12px;
  }
  .content2-2a3{
    float: right;
    color: #a1a2a3;
    font-size: 12px;
  }
  .content2-2a2{
    float: right;
    width: 15px;
    margin-left: 5px;
  }
  .content2-2a4{
    float: right;
    color: #a1a2a3;
    font-size: 12px;
    margin-right: 15px;
    display: none;
  }
  .you-footer1{
    width: 100%;
    border: none;
    outline: none;
    font-size: 14px;
  }
  .you-footer2{
    overflow: hidden;
  }
  .you-footer2a{
    float: left;
    display: none;
  }
  .you-footer2b{
    float: right;
    display: none;
  }
</style>
