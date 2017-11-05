<template>
  <div id="news-xia-zai" v-if="isShowXia">
    <!--下载App-->
    <div class="wrap-A" @click="closeXia"></div>
    <div class="wrap">
      <img src="../../assets/xiazai.png" alt="">
    </div>
  </div>
</template>

<script>
    export default {
        name: '',
      data(){
          return{
            isShowXia:true
          }
      },
      methods:{
        closeXia:function () {
          this.isShowXia =false;
          this.$emit('closeXiaZai')
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
