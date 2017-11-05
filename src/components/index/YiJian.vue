<template>
  <div id="yi-jian" v-if="isShowYijian">
    <!--尾部：意见栏-->
    <div class="wrap-A" @click="closeyi"></div>
    <div class="wrap">

      <div class="header">
        <div class="header-a">意见反馈</div>
      </div>

      <div class="content">
        <textarea name="feedback" placeholder="你有啥想ZUO的，快告诉我们呀~" class="content1"></textarea>
        <button class="footer">提交反馈</button>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: '',
      data(){
          return{
            isShowYijian:true
          }
      },
      methods:{
        closeyi:function () {
          this.isShowYijian =false;
          this.$emit('closeyijian')
        }
      }
    }
</script>

<style scoped>
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
    width: 540px;
    margin: 0 auto;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
  }
  .header {
    width: 100%;
    height: 75px;
    background-color: #272c2f;
    text-align: center;
    line-height: 82px;
    position: relative;
    font-size: 18px;
    color: #fff;
  }
  .content {
    width: 100%;
    background-color: white;
    padding: 30px;
    box-sizing: border-box;
    border-radius: 4px;
  }
  .content1{
    border: 1px solid #ececec;
    width: 100%;
    height: 186px;
    background-color: #f6f6f6;
    resize: none;
    outline:none;
    padding: 15px;
    box-sizing: border-box;
  }
  .footer{
    margin-top: 20px;
    width: 100%;
    height:50px;
    background-color: #1fd7e2;
    color: #fff;
    font-size: 18px;
    box-sizing: border-box;
  }
</style>
