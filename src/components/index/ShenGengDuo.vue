<template>
  <div id="shen-geng-duo" v-if="thisdata != null">
    <!--深度：更多文章-->
    <div class="wrap">
      <div class="header">更多文章</div>

      <div class="content">
        <div class="content1" v-for="article in thisdata['articles']" @click="shengeng11">
          <div class="content1-a">
            <a href="###"><img :src="article['banner']" alt=""></a>
          </div>
          <div class="content1-b">
            <a href="">
              <div class="content1-b1">{{article['title']}}</div>
            </a>
            <div class="content1-b2">
              <span class="b1-zuo">ZUO先生</span>
              <span class="b1-you">{{article['timeAgo']}}</span>
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
        axios.get('api/articles').then(function (res) {
          that.thisdata =res.data;
        })
      },
      methods:{
        shengeng11:function () {
          this.$emit('openshengengduo11')
        }
      }
    }
</script>

<style scoped>
#shen-geng-duo{
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
  .content{
    width: 100%;
    display: -webkit-inline-flex;
    justify-content: space-between;
    flex-wrap: wrap;
    box-sizing: border-box;
    margin-bottom: 30px;
  }
  .content1{
    width:219px;
    box-sizing: border-box;
    margin-bottom:20px ;
    overflow: hidden;
    border-radius: 5px;
  }
  .content1:hover{
    box-shadow: 0px 0px 0px 6px rgb(240,240,240),0 1px 3px 6px rgb(239,239,239);
  }
  .content1-a{
    width:219px;
    height: 162px;
  }
  .content1-a img{
    width:100%;
    height: 100%;
    object-fit:cover;
  }
  .content1-b{
    padding: 15px;
    background-color: #fff;
  }
  .content1-b1{
    height: 105px;
    font-size: 14px;
    color: #272c2f;
    line-height: 20px;
  }
  .content1-b{
    width: 100%;
  }
  .content1-b2{
    width: 100%;
    padding-bottom: 20px;
  }
  .b1-zuo{
    font-size: 12px;
    float: left;
    color: #272c2f;
  }
  .b1-you{
    font-size: 12px;
    float: right;
    color: #a6a7a7;;
  }
</style>
