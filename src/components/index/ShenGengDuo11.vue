<template>
  <div id="shen-geng-duo11" v-if="thisdata !=null">
    <!--点击更多文章出现的二级页面-->
    <div class="wrap">

      <div class="header" v-for="article in thisdata['articles']">
        <div class="header-A">
          <img :src="article['banner']" alt="" class="header1">
          <div class="header2"></div>
          <div class="header3">
            <div class="header3-a">
              <h1>{{article['title']}}</h1>
            </div>
            <div class="header3-b">
              <span>{{article['sceneTagName']}}</span>
              <a v-for="tag in article['tags']">
                <span>{{tag}}</span>
              </a>
            </div>
            <div class="header3-c">
              <div class="header3-c1">
                <div href="" class="c1-a">ZUO先生</div>
                <img src="../../assets/i.png" alt="" class="c1-b">
                <div class="c1-c">{{article['timeAgo']}}</div>
              </div>
              <div class="header3-c2">
                <div class="zuo">
                  <img src="../../assets/heart.png" alt="" class="c2-a">
                  <div class="c2-b">{{article['likesCount']}}</div>
                </div>
                <div class="you">
                  <img src="../../assets/duihua1.png" alt="" class="c2-a1">
                  <div class="c2-b1">{{article['commentCount']}}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="content" v-for="article in thisdata['articles']">
        <div class="content1" v-html="article['content']"></div>
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
      axios.get('api/articles').then(function (res) {
        that.thisdata = res.data;
      })
    }
  }
</script>

<style scoped>
  .header {
    position: relative;
    text-align: center;
  }

  .header1 {
    width: 100%;
    height: 400px;
    object-fit: cover;
  }

  .header2 {
    width: 100%;
    height: 400px;
    background-color: rgba(45, 47, 49, 0.6);
    position: absolute;
    left: 0;
    top: 0;
  }

  .header3 {
    width: 670px;
    position: absolute;
    position: absolute;
    left: 50%;
    top: 85%;
    transform: translate(-50%, -85%);
  }

  .header3-a h1 {
    font-size: 30px;
    border-bottom: none;
    color: #fff;
  }

  .header3-b {
    text-align: center;
    margin-top: 30px;
    margin-bottom: 30px;
  }

  .header3-b span {
    color: #a6a7a7;
    margin-right: 30px;
  }

  .header3-c {
    overflow: hidden;
    padding-top: 18px;
    padding-bottom: 18px;
    border-top: 1px solid rgba(255, 255, 255, 0.5);
  }

  .header3-c1 {
    float: left;
    background-image: url(../../assets/zuo.png);
    -webkit-background-size: 30px;
    background-size: 30px;
    background-position: 0 -5px;
    padding-left: 40px;
  }

  .header3-c2 {
    float: right;
  }
  .zuo{
    float: left;
  }
  .you{
    float: left;
  }
  .c1-a {
    color: #fff;
    font-size: 14px;
    float: left;
    margin-right: 5px;
    margin-top: 5px;
  }

  .c1-b {
    width: 25px;
    float: left;
  }

  .c1-c {
    margin-left: 20px;
    color: rgba(255, 255, 255, 0.9);
    float: left;
    font-size: 13px;
    margin-top: 5px;
  }

  .c2-a {
    width: 23px;
    float: left;
    margin-right: 10px;
  }
  .c2-a1 {
    width: 20px;
    float: left;
    margin-right: 10px;
  }

  .c2-b {
    float: left;
    color: #b8b9b9;
    margin-right: 15px;
  }
  .c2-b1 {
    float: left;
    color: #b8b9b9;
  }
  .content1{
    width: 670px;
    margin:0 auto;
    margin-top: 40px;
    /*text-align: center;*/
    border-left: none;
    font-style: inherit;
  }
</style>
