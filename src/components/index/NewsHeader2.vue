<template>
  <div class="news-header2">
    <!--创建zuo账号-->
    <div id="footer">
      <div class="footer-AA">
        <div class="footer-A">
          <h1 class="footer1">可能是全宇宙最ZUO的图片社区</h1>
          <div class="footer2">
            <span class="footer2-a">和像你一样认真对待生活的人一起 </span>
            <br>
            <span class="footer2-b">从设计的视角，重新认识世界</span>
          </div>
          <button class="footer3">创建zuo帐号</button>
          <img src="../../assets/cha.png" alt="" class="cha">
          <a href=""><div class="footer3-1">下载iOS版ZUO App</div></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: ''
    }
</script>

<style scoped>
  #footer{
    height: 214px;
    width: 100%;
    margin: 0 auto;
    text-align: center;
    background-image: url(../../assets/bgc.jpg);
    background-repeat:repeat;
    padding-right: 30px;
    position: relative;
  }
  .footer-AA{
    width: 56%;
    text-align: center;
    margin: 0 auto;
  }
  .footer-A{
    max-width: 790px;
    margin: 0 auto;
    text-align: center;
    box-sizing: border-box;
  }
  .footer1{
    font-size: 24px;
    padding-top: 30px;
    font-weight: 700;
    color: #272c2f;
    border-bottom: none;
    margin: 0;
  }
  .footer2{
    margin-top: 20px;
  }
  .footer2-a{
    font-size: 16px;
    color: #5d6c75;
  }
  .footer2-b{
    font-size: 16px;
    color: #5d6c75;
  }
  .footer3{
    background-color: #1fd7e2;
    color: #fff;
    width: 200px;
    height: 44px;
    font-size: 16px;
    border: none;
    cursor: pointer;
    border-radius: 4px;
    margin-top: 20px;
  }
  .footer3-1{
    display: none;
    background-color: #272c2f;;
    color: #fff;
    width: 240px;
    height: 44px;
    font-size: 16px;
    border-radius: 4px;
    box-sizing: border-box;
    padding: 10px;
  }
  .cha{
    position: absolute;
    right:35px;
    top:0;
    padding-top: 30px;
    width:20px;
  }
  @media screen and (max-width:562px){
    #footer{
      max-width: 562px;
      min-width:385px
    }
    .footer-AA{
      width: 90%;
    }
    .footer-A{
      max-width: 543px;
      min-width: 345px;
    }
    .footer1{
      font-size:20px;
    }
    .footer2{
      margin-bottom: 20px;
    }
    .footer2 span{
      font-size:13px;
    }
    .footer3{
      display: none;
    }
    .footer3-1{
      display: block;
      margin: 0 auto;
    }
    .cha{
      display: none;
    }
  }
  @media screen and (max-width: 890px){
    .cha{
      display: none;
    }
    .footer3{
      display: none;
    }
  }
</style>
