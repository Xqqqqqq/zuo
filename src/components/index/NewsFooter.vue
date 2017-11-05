<template>
  <div id="news-footer">
    <!--首页尾部，点击出现二级页面-->
    <div class="footer">
      <div class="footer1">
        <a href="###" @click="openGong">关注公众号</a>
        <a href="###">关于ZUO</a>
        <a href="###" @click="openYi">反馈吐槽</a>
      </div>
      <div class="footer2">
        <span>上海设慧网络科技有限公司2016版权所有</span>
        <span>沪ICP备15013372号</span>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: '',
      methods:{
          openGong:function () {
            this.$emit('opengongzhong')
          },
        openYi:function () {
          this.$emit('openyijian')
        }
      }
    }
</script>

<style scoped>
  #news-footer{
    width: 100%;
    background-color: rgb(229,229,229);
  }
  a{
    text-decoration: none;
  }
  .footer{
    width: 420px;
    margin: 0 auto;
    background-color: rgb(229,229,229);
    padding-top: 20px;
    padding-bottom: 20px;
  }
  .footer1{
    width: 100%;
    text-align: center;
    margin-bottom: 10px;
  }
  .footer1 a{
    font-size: 13px;
    color: #999a9a;
    margin-right: 30px;
  }
  .footer2{
    width: 100%;
    text-align: center;
  }
  .footer2 span{
    font-size: 13px;
    color: #b8b9b9;
    margin-right: 10px;
  }
</style>
