<template>
  <div id="shen-tui-jian" v-if="thisdata != null">
    <!--深度：推荐阅读-->
    <div class="wrap">
      <div class="header">推荐阅读</div>

      <div class="content">
          <div class="content1" v-for="(hot_article,index) in thisdata['hot_articles']" @click="shentui1">
            <img :src="hot_article['banner']" alt="" class="content1-a">
            <div class="content1-b">
              <a href="">
              <div class="content1-b1">{{hot_article['title']}}</div>
              <div class="content1-b2">{{hot_article['summary']}}</div>
              </a>
            </div>
            <div class="content1-c">
              <div class="content1-czuo">
                <!--<img src="../../assets/landian.png" alt="">-->
                <a href="###" class="czuo2">{{hot_article['sceneTagName']}}</a>
              </div>
              <div class="content1-cyou">
                <span class="cyou1">{{hot_article['timeAgo']}}</span>
              </div>
            </div>
            <a href="###"><div class="content1-mask"></div></a>
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
        thisdata:null
      }
    },
    mounted() {
      var that = this;
      axios.get('api/hot_articles').then(function (res) {
        that.thisdata = res.data;
      })
    },
    methods:{
      shentui1:function () {
        this.$emit('openshentuijian1')
      }
    }
  }
</script>

<style scoped>
  #shen-tui-jian {
    width: 930px;
    margin: 0 auto;
  }
  a{
    text-decoration: none;
  }
  .header {
    width: 100%;
    text-align: center;
    font-size: 22px;
    font-weight: 700;
    padding-top: 30px;
    padding-bottom: 30px;
  }

  .content {
    width: 100%;
    display: -webkit-inline-flex;
    justify-content: space-between;
    flex-wrap: nowrap;
    box-sizing: border-box;
  }

  .content1 {
    width: 298px;
    box-sizing: border-box;
    position: relative;
    border-radius: 4px;
    overflow: hidden;
  }
  .content1-mask{
    width: 298px;
    height: 456px;
    background-color: rgba(45,47,49,0.4);
    position: absolute;
    top: 0;
    left: 0;
    border-radius: 4px;
    overflow: hidden;
  }
  .content1-mask:hover{
    background-color: rgba(45,47,49,0.7);
    transition: all 0.5s;
  }
  .content1-b{
    margin-bottom: 18px;
    padding-left: 18px;
    padding-right: 18px;
    width: 100%;
    box-sizing: border-box;
    position: absolute;
    left: 0;
    bottom:65px;
    z-index: 10;
  }
  .content1-b1 {
    font-size: 18px;
    color: #fff;
    margin-bottom: 10px;
  }
  .content1-b2{
    font-size: 14px;
    font-weight: 400;
    color: rgba(255,255,255,0.8);
    padding-top: 10px;
  }
  .content1-c{
    border-top: 1px solid rgba(255,255,255,0.2);
    overflow: hidden;
    position: absolute;
    bottom: -4px;
    left: 0;
    padding: 18px;
    width: 100%;
    z-index: 10;
  }
  .content1-czuo{
    float: left;
  }
  .czuo2{
    color:white;
    font-size:14px;
  }
  .content1-cyou{
    float: right;
  }
  .cyou1{
    color: white;
    font-size:13px;
  }
</style>
