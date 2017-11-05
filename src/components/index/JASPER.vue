<template>
  <div id="JASPER" v-if="thisdata != null">
    <!--热门标签中每一个-->
    <div class="wrap">
      <!--头部，搜索-->
      <div class="header">
        <div class="header1">
          <div class="header1-a">搜索:{{thisdata['posts'][0]['topicTags']}}</div>
          <div class="header1-b">{{thisdata['posts'][0]['topicTags']}}</div>
        </div>
      </div>

      <div class="top">相关ZUO</div>
      <!--每一小块-->
      <div class="content1">
        <div class="content" >
          <div class="zhong" v-for="post in thisdata['posts']">
            <!--图片-->
            <div class="zhong1">
              <div class="zhong1-a">
                <span class="a1-1">来自</span>
                <a href="###" class="a1-2">{{post['owner']['username']}}</a>
              </div>
              <div class="zhong1-b">
                <img :src="post['postImage']['url']" alt="">
              </div>
              <div class="zhong1-c">
                <div class="c1-1">
                  <a href="###" class="c1-11">{{post['sceneTag']['name']}}</a>
                  <a href="###" class="c1-12" v-html="post.topicTags"></a>
                </div>
                <div class="c1-2">
                  <div class="c1-21">
                    <div class="c1-zuo">
                      <img src="../../assets/yuanquan.png" alt=""/>
                      <div>{{post['likeCount']}}</div>
                    </div>
                    <div class="c1-you">
                      <img src="../../assets/duihua1.png" alt=""/>
                      <div>{{post['commentedCount']}}</div>
                    </div>
                  </div>
                  <div class="c1-22">
                    <img src="../../assets/zhuanfa.png" alt=""/>
                  </div>
                </div>
              </div>
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
    data() {
      return {
        thisdata: null
      }
    },
    mounted() {
      var that = this;
      axios.get('api/search/posts?q=JASPER+MORRISON').then(function (res) {
        that.thisdata = res.data;
      })
    }
  }
</script>

<style scoped>
  #JASPER {
    background-color: rgb(244, 244, 244);
  }

  .header {
    width: 100%;
    height: 120px;
    background-color: white;
    padding-top: 20px;
    padding-bottom: 20px;
    box-sizing: border-box;
  }

  .header1 {
    width: 930px;
    margin: 0 auto;
  }

  .header1-a {
    background-image: url(../../assets/fangda.png);
    background-size: 20px;
    background-repeat: no-repeat;
    background-position: 0 4px;
    padding-left: 28px;
    font-size: 18px;
    font-weight: 500;
    color: #272c2f;
    margin-bottom: 20px;
  }

  .header1-b {
    background-image: url(../../assets/landian.png);
    background-size: 10px;
    background-repeat: no-repeat;
    background-position: 5px 5px;
    padding-left: 29px;
    color: #a6a7a7;
  }

  .top {
    font-size: 20px;
    font-weight: 700;
    text-align: center;
    padding-top: 30px;
    padding-bottom: 30px;
  }

  .content1{
    text-align: center;
  }

  .content {
    text-align: left;
    margin: 0 auto;
    width: 930px;
    display: -webkit-inline-flex;
    justify-content: space-between;
    flex-wrap: wrap;
    /*box-sizing: border-box;*/
  }

  .zhong1 {
    width: 219px;
    background-color: rgb(244, 244, 244);
    margin-bottom: 20px;
  }
  .zhong1:hover{
    box-shadow: 1px 1px 2px 5px rgb(235,235,235),2px 2px 2px 7px rgb(239,239,239);
  }

  .zhong1-a {
    background-color: white;
    padding: 12px 10px;
  }

  .a1-1 {
    color: #a6a7a7;
    font-size: 14px;
  }

  .a1-2 {
    color: black;
    font-size: 14px;
    text-decoration: none;
  }

  .zhong1-b {
    width: 100%;
    height: 219px;
    background-color: rgb(244, 244, 244);
  }

  .zhong1-c {
    background-color: white;
  }

  .c1-1 {
    padding: 10px;
    border-bottom: 1px solid #ececec;
    box-sizing: border-box;
    width: 100%;
  }

  .c1-1 a {
    color: #a6a7a7;
    font-size: 13px;
    text-decoration: none;
    margin-right: 10px;
  }

  .c1-1 a:hover {
    color: black;
  }

  .c1-2 {
    padding: 10px;
    overflow: hidden;
  }

  .c1-21 {
    float: left;
  }

  .c1-22 {
    float: right;
  }
  .c1-22 img{
    width: 20px;
  }

  .c1-zuo {
    float: left;
    margin-right: 25px;
  }
  .c1-zuo img{
    width: 20px;
    float: left;
    margin-right: 6px;
  }
  .c1-zuo div{
    float: left;
    margin-top:-2px;
  }
  .c1-you {
    float: left;
  }
  .c1-you img{
    width: 18px;
    float: left;
    margin-right: 6px;
  }
  .c1-you div{
    float: left;
    margin-top: -2px;
  }
</style>
