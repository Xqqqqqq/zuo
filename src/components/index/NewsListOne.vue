<template>
  <div id="news-list-one" v-if="thisdata != null">
    <!--左边第一块：话题栏部分-->
    <div class="wrap" @click="openlist1">
      <div class="header">
        <div class="header1">话题</div>
        <div class="header2"></div>
        <div class="header3">
          <span class="header3-a" >{{thisdata['topic']['title']}}</span>
          <img src="../../assets/jiantou.png" alt="" class="header3-b">
        </div>
        <a href="" class="header4">
          <span>{{thisdata['topic']['collect_count']}}人收藏 &nbsp | &nbsp</span>
          <span>{{thisdata['topic']['collect_count']}}个讨论</span>
        </a>
        <img :src="thisdata['topic']['cover']" alt="" class="header5">
        <div class="header6"></div>
      </div>

      <a href="###" class="footer-AA">
        <div class="footer">
            <a href="" class="footer-a">{{username1}}:</a>
            <span v-html="text1" class="footer-b"></span>
        </div>
      </a>

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
//      设置话题栏下评论初始未0
      index:'0',
      username1:'',
      text1:''
    }
  },
  mounted(){
    var that=this;
    axios.get('api/topics').then(function (res) {
      that.thisdata = res.data;
//      因每次刷新不一样，设置随机出现
      that.index=rand(0,4);
      that.username1 =that.thisdata.topic.comments[that.index].author.username;
      that.text1 =that.thisdata.topic.comments[that.index].text;
      console.log(that.thisdata);
    })
  },
  methods:{
    openlist1:function () {
      this.$emit('openlistone1')
    }
  },
  created(){
    var that= this;
    var timer =setInterval(function () {
//      如果到第四个则重新返回第一个
      if(that.index == 4){
        that.index = 0;
        axios.get('api/topics').then(function (res) {
          that.username1 =that.thisdata.topic.comments[that.index].author.username;
          that.text1 =that.thisdata.topic.comments[that.index].text;
        })
      }else{
        that.index++;
        axios.get('api/topics').then(function (res) {
          that.username1 =that.thisdata.topic.comments[that.index].author.username;
          that.text1 =that.thisdata.topic.comments[that.index].text;
        })
      }
    },10000)
  }
}
function rand(min,max) {
  return Math.floor(Math.random()*(max-min+1)+min)
}
</script>

<style scoped>
#news-list-one{
  margin-top: 30px;
  float: left;
}
a{
  text-decoration: none;
}
.wrap{
  width: 540px;
}
  .header{
    width: 100%;
    height: 166px;
    border-radius: 4px 4px 0 0;
    position: relative;
    box-sizing: border-box;
    overflow: hidden;
  }
  .header1{
    color: white;
    font-size:14px;
    position: absolute;
    left: 30px;
    top:20px;
    z-index: 2;
  }
.header2{
  width: 20px;
  height: 5px;
  border-radius: 6px;
  background-color: #F8D440;
  margin-top: 10px;
  position: absolute;
  left: 30px;
  top:43px;
  z-index: 2;
}
.header3{
  color: white;
  font-size:22px;
  position: absolute;
  left: 30px;
  top:80px;
  z-index: 2;
}
.header3-b{
  width: 23px;
  position: absolute;
  left: 138px;
  top:3px;
  z-index: 2;
}
.header4{
  text-decoration: none;
  color: white;
  font-size:14px;
  position: absolute;
  left: 30px;
  top:140px;
  z-index: 2;
}
.header6{
  width: 100%;
  height: 180px;
  border-radius: 6px 6px 0 0;
  background-color: rgba(25,22,18,0.5);
  position: absolute;
  top:0;
  left: 0;
}
.footer-AA{
  text-decoration: none;
  background-color: white;
}
  .footer{
    width: 100%;
    height: 80px;
    background-color: white;
    border-radius: 0 0 4px 4px;
    padding: 18px 20px;
    box-sizing: border-box;
    overflow: hidden;
  }
  .footer-a{
    color:#272c2f;
    font-size:13px;
  }
.footer-b{
  color: #999a9a;
  font-size:13px;
}
</style>

