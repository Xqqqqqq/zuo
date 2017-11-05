<template>
  <div id="news-list-one1" v-if="thisdata != null">
    <!--点击话题后的二级页面-->

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
        axios.get('api/topic/575bb18e6be3ff0069503da2').then(function (res) {
          that.thisdata =res.data;
        })
      }
    }
</script>

<style scoped>

</style>
