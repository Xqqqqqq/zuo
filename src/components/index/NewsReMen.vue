<template>
  <div id="news-re-men" v-if="thisdata != null">
    <!--右侧热门标签-->
    <div class="header">热门标签</div>
    <span class="content" v-for="(hotTag,index) in thisdata['hot_tags']">
      <!--ref：按引用将参数传递给方法-->
      <a href="###" id="content-a" @click="openJasper" ref="color1" @mouseover="mouseover1(index)" @mouseout="mouseout1(index)">{{hotTag['content']}}</a>
    </span>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: '',
    data() {
      return {
        thisdata: null,
      }
    },
    mounted() {
      var that = this;
      axios.get('api/web_hot_tags').then(function (res) {
        that.thisdata = res.data
      })
    },
    methods:{
      openJasper:function () {
        this.$emit('openJASPER')
      },
      mouseover1:function (ev) {
        this.$refs.color1[ev].style.backgroundColor='rgb(135,137,138)';
        this.$refs.color1[ev].style.color='white';
      },
      mouseout1:function (ev) {
        this.$refs.color1[ev].style.backgroundColor='#eaeced';
        this.$refs.color1[ev].style.color='#999b9c';
      }
    }
  }
</script>

<style scoped>
#news-re-men{
  width: 220px;
  float: left;
  margin-left: 30px;
  margin-top: 30px;
}
  .header{
    font-size:14px;
    color: black;
    margin-bottom: 20px;
  }
  .content a{
    margin-right: 10px;
    margin-bottom: 10px;
    padding: 6px 10px;
    font-size: 14px;
    color: #999b9c;
    background-color: #eaeced;
    border-radius: 4px;
    display: inline-block;
    text-decoration: none;
  }
  /*.content a:hover{*/
    /*background-color:rgb(135,137,138);*/
    /*color: white;*/
    /*transition: all 0.5s;*/
  /*}*/
</style>
