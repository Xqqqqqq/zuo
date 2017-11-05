<template>
  <div id="gong-zhong-hao" v-if="isShowGong">
    <!--尾部：公众号部分-->
    <div class="wrap-A" @click="closeGong"></div>
    <div class="wrap">
      <img src="../../assets/wechat.png" alt="">
    </div>
  </div>
</template>

<script>
  export default {
    name: '',
    data(){
      return{
        isShowGong:true
      }
    },
    methods:{
      closeGong:function () {
        this.isShowGong =false;
        this.$emit('closegongzhong')
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
    width: 436px;
    margin: 0 auto;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
  }
  .wrap img{
    width: 100%;
  }
</style>
