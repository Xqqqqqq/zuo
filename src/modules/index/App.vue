<template>
  <!--全部内容-->
  <div id="one">
    <!--导航栏-->
    <news-header @openzhuce="ozhuce" @opendenglu="odenglu" @openxiazai="oxiazai" @openzong="ozong"
                 @openshendu="oshendu"></news-header>
    <!--导航栏下-->
    <news-header2 v-if="abc"></news-header2>

    <!--导航栏下首页内容-->
    <div class="zong" v-if="zong">
      <news-list-one @openlistone1="olistone1"></news-list-one>
      <!--热门标签-->
      <news-re-men @openJASPER="oJASPER"></news-re-men>
      <news-list-two @openhaosheji="ohaosheji" @closehaosheji="chaosheji" @openhuaisheji="ohuaisheji"
                     @closehuaisheji="chuaisheji" @opennewslist2="onewslist2"></news-list-two>
      <!--推荐关注-->
      <news-tui-jian></news-tui-jian>
      <!--好 坏 设计-->
      <hao-she-ji v-if="hao"></hao-she-ji>
      <huai-she-ji v-if="huai"></huai-she-ji>
    </div>
    <div class="clear"></div>
    <!--点击左边第一个的二级页面-->
    <news-list-one1 v-if="listone1"></news-list-one1>
    <!--点击热门标签下的二级页面-->
    <JASPER v-if="jasper"></JASPER>

    <!--登录 注册 下载App 页面-->
    <news-deng-lu v-if="isSee" @closedenglu="cdenglu" @openzhuce="ozhuce" @openwangji="owangji"></news-deng-lu>
    <news-deng-lu2 v-if="isSee2" @closedenglu2="cdenglu2"></news-deng-lu2>
    <news-zhu-ce v-if="issee" @closezhuce="czhuce" @opendenglu="odenglu"></news-zhu-ce>
    <news-xia-zai v-if="isWatch" @closeXiaZai="cXiaZai"></news-xia-zai>

    <!--深度页面一二级页面-->
    <div class="shen" v-if="shen" @openshendu="oshendu">
      <!--深度页面一级页面-->
      <div class="shen" v-if="shenSee">
        <shen-tui-jian @openshentuijian1="oshentuijian1"></shen-tui-jian>
        <shen-geng-duo @openshengengduo11="oshengengduo11"></shen-geng-duo>
        <!--<news-footer v-if="gd2"></news-footer>-->
      </div>
      <!--深度页面二级页面-->
      <shen-tui-jian1 v-if="shentui1" ></shen-tui-jian1>
      <shen-geng-duo11 v-if="shengeng11"></shen-geng-duo11>
    </div>

    <!--尾部-->
    <news-footer @opengongzhong="ogongzhong" @openyijian="oyijian"></news-footer>
    <gong-zhong-hao v-if="gongzhong" @closegongzhong="cgongzhong"></gong-zhong-hao>
    <yi-jian v-if="yijian" @closeyijian="cyijian"></yi-jian>
    <news-list-two2 v-if="list2" @closelist2="clist2"></news-list-two2>
  </div>
</template>

<script>
  import NewsHeader from '../../components/index/NewsHeader'
  import NewsHeader2 from '../../components/index/NewsHeader2'
  import NewsListOne from '../../components/index/NewsListOne'
  import NewsListTwo from '../../components/index/NewsListTwo'
  import HaoSheJi from '../../components/index/HaoSheJi'
  import HuaiSheJi from '../../components/index/HuaiSheJi'
  import NewsReMen from '../../components/index/NewsReMen'
  import NewsTuiJian from '../../components/index/NewsTuijian'
  import NewsFooter from '../../components/index/NewsFooter'
  import NewsDengLu from '../../components/index/NewsDengLu'
  import NewsDengLu2 from '../../components/index/NewsDengLu2'
  import NewsZhuCe from '../../components/index/NewsZhuCe'
  import NewsXiaZai from '../../components/index/NewsXiaZai'
  import ShenTuiJian from '../../components/index/ShenTuiJian'
  import ShenTuiJian1 from '../../components/index/ShenTuiJian1'
  import ShenGengDuo from '../../components/index/ShenGengDuo'
  import ShenGengDuo11 from '../../components/index/ShenGengDuo11'
  import JASPER from '../../components/index/JASPER'
  import NewsListOne1 from '../../components/index/NewsListOne1'
  import GongZhongHao from '../../components/index/GongZhongHao'
  import YiJian from '../../components/index/YiJian'
  import NewsListTwo2 from '../../components/index/NewsListTwo2'

  export default {
    name: 'index',
    components: {
      NewsHeader,
      NewsHeader2,
      NewsListOne,
      NewsListTwo,
      HaoSheJi,
      HuaiSheJi,
      NewsReMen,
      NewsTuiJian,
      NewsDengLu,
      NewsDengLu2,
      NewsZhuCe,
      NewsXiaZai,
      ShenTuiJian,
      ShenTuiJian1,
      ShenGengDuo,
      NewsFooter,
      ShenGengDuo11,
      JASPER,
      NewsListOne1,
      GongZhongHao,
      YiJian,
      NewsListTwo2
    },
    data() {
      return {
        issee: false,
        isSee: false,
        isSee2: false,
        isWatch: false,
        abc: true,
        zong: true,
        istui: false,
        isgeng: false,
        shen: false,
        shenSee:true,
        hao: false,
        huai: false,
        shentui1: false,
        shengeng11:false,
        jasper:false,
        listone1:false,
        gongzhong:false,
        yijian:false,
        list2:false
      }
    },
    methods: {
      odenglu: function () {
        this.isSee = true;
      },
      cdenglu: function () {
        this.isSee = false;
      },
      ozhuce: function () {
        this.issee = true;
      },
      czhuce: function () {
        this.issee = false;
      },
      oxiazai: function () {
        this.isWatch = true;
      },
      owangji: function () {
        this.isSee2 = true
      },
      cdenglu2: function () {
        this.isSee2 = false;
      },
      ozong: function () {
        this.zong = true;
        this.abc = true;
        this.shen = false;
        this.jasper =false;
        this.listone1 =false;
      },
      oshendu: function () {
        this.zong = false;
        this.shen = true;
        this.abc = false;
        this.shentui1 =false;
        this.shenSee =true;
      },
      cXiaZai: function () {
        this.isWatch = false
      },
      ohaosheji: function () {
        this.hao = true;
      },
      chaosheji: function () {
        this.hao = false;
      },
      ohuaisheji: function () {
        this.huai = true;
      },
      chuaisheji: function () {
        this.huai = false;
      },
      oshentuijian1: function () {
        this.shentui1 = true;
        this.shenSee =false;
      },
      oshengengduo11:function () {
        this.shengeng11=true;
        this.shenSee =false;
      },
      oJASPER:function () {
        this.jasper=true;
        this.zong=false;
        this.abc=false;
      },
      olistone1:function () {
        this.listone1=true;
        this.abc=false;
        this.zong =false
      },
      ogongzhong:function () {
        this.gongzhong=true;
      },
      cgongzhong:function () {
        this.gongzhong=false
      },
      oyijian:function () {
        this.yijian =true
      },
      cyijian:function () {
        this.yijian =false
      },
      onewslist2:function () {
        this.list2=true
      },
      clist2:function () {
        this.list2=false
      }
    }
  }
</script>

<style scoped>
  @import "../../common/style/marx.min.css";

  .zong {
    width: 800px;
    margin: 0 auto;
  }
  .clear{
    clear: both;
  }

  #one {
    background-color: rgb(244, 244, 244);
  }

  html {
    background-color: red;
  }
</style>
