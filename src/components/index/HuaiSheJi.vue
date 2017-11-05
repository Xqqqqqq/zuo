<template>
  <div id="huai-she-ji" v-if="thisdata !=null">
    <!--坏设计-->
    <div class="wrap">

      <div class="content" >
        <!--每一小块内容-->
        <div class="content1" v-for="post in thisdata['posts']">
          <!--用户名-->
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

          <!--中间部分：图片-->
          <div class="zhong">
            <img :src="post['postImage']['url']" alt="" class="zhong-A">
            <div class="zhong-AA"></div>
            <div class="zhong-BB" :style="{left:post.haloCenterRatio.width_ratio*100+'%',top:(post.haloCenterRatio.height_ratio)*100+'%'}"></div>
            <div class="zhong-B" :style="{left:post.haloCenterRatio.width_ratio*100+'%',top:(post.haloCenterRatio.height_ratio)*100+'%'}">
              <div class="zhong-B1">赞同</div>
              <div class="zhong-B2">这个态度</div>
            </div>
          </div>
          <!--下：设计，文字部分-->
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

            <div class="xia-C">
              <div class="xia-C1">
                <span class="xia-C1-b">{{post['commentedCount']}}条评论</span>
              </div>
              <input type="text" class="xia-C3" placeholder="写下你的评论...">

            </div>

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
        thisdata:null
      }
    },
    mounted(){
      var that =this;
      axios.get('api/posts?design=good&scene=%E5%85%A8%E9%83%A8').then(function (res) {
        that.thisdata=res.data
      })
    }
  }
</script>

<style scoped>
  #huai-she-ji{
    float: left;
  }
  .wrap{
    width: 540px;
  }
  .content {
    width: 100%;
    margin-top: 20px;
  }

  .content1 {
    background-color: white;
    position: relative;
    margin-bottom: 30px;
  }
  @-webkit-keyframes move2{
    from{
      transform:translate(0,0);
    }
    to{
      transform:translate(-50px,0);
    }
  }
  .shang {
    overflow: hidden;
    padding: 10px 15px 0px 15px;
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
    border: 1px solid #1fd7e2;;
    background-color: rgba(31,217,255,0.2);
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
    border: 1px solid #1fd7e2;;
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
    padding-bottom: 20px;
    border-bottom: 1px solid rgb(231, 231, 231);
  }

  .xia-C1-b {
    color: #a6a7a7;
    margin-left: 8px;
    margin-right: 10px;
    font-size: 14px;
  }

  li:hover{
    background-color: red;
  }
  .xia-C3 {
    width: 100%;
    border: none;
    outline: none;
    font-size: 14px;
  }
</style>
