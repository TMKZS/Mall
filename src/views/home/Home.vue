<!--  -->
<template>
  <div id='home'>
    <nab-bar class="home-nav"><div slot="center">购物车</div></nab-bar>

    <tab-control :titles="['流行', '新款', '精选']"
                   @tabClick="tabClick"
                   ref="tabControl1"
                   class="tab-control"
                   v-show = "isTabFixed"/>

    <scroll class="content"
    ref="scroll"
    :probe-type='3'
    @scroll="contentStroll"
    :pull-up-load="true"
    @pullingUp = "loadMore"
    >
      <home-swiper :banners= "banners"
                   @swiperImageLoad="swiperImageLoad"
      ></home-swiper>
      <recommend-view :recommends= "recommends"></recommend-view>
      <feature-view/>
      <tab-control :titles="['流行', '新款', '精选']"
                   @tabClick="tabClick"
                   ref="tabControl2"/>
      <goods-list :goods= "showGoods"/>
    </scroll>
    <back-top @click.native="backClick" v-show="isShowBackTop"/>


  </div>
</template>

<script>

import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/RecommendView'
import FeatureView from './childComps/FeatureView'

import NabBar from 'components/common/navbar/NavBar'
import TabControl from 'components/content/tabControl/TabControl'
import GoodsList from 'components/content/goods/GoodsList'
import Scroll from 'components/common/scroll/Scroll'
import BackTop from 'components/content/backtop/BackTop'

import {getHomeMultidata,getHomeGoods} from 'network/home'
import {debounce} from 'common/utils'



export default {
  name:'Home',
  data () {
    return {
      banners: [],
      recommends:[],
      goods: {
        'pop': {page: 0, list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []}
      },
      currentType:'pop',
      isShowBackTop: false,
      tabOffsetTop: 0,
      isTabFixed: false,
      saveY: 0,
    };

  },

  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,

    NabBar,
    TabControl,
    GoodsList,
    Scroll,
    BackTop
  },

  computed: {
    showGoods(){
      return this.goods[this.currentType].list
    }
  },


  methods: {
    /*
      方法
    */
    tabClick(index){
      switch (index) {
          case 0:
          this.currentType = 'pop'
          break;
          case 1:
          this.currentType = 'new'
          break;
          case 2:
          this.currentType = 'sell'
          break;
      }
      this.$refs.tabControl1.currentIndex = index;
      this.$refs.tabControl2.currentIndex = index;
    },
    backClick(){
      this.$refs.scroll.scrollTo(0,0)
    },

    contentStroll(position){
      this.isShowBackTop = (-position.y) > 1000;
      this.isTabFixed = (-position.y) > this.tabOffsetTop;
    },
    loadMore(){
      this. getHomeGoods(this.currentType)

    },

    swiperImageLoad(){
      //2.获取tabControl的offsetTop，获取当前元素到父元素的距离
        this.tabOffsetTop = this.$refs.tabControl2.$el.offsetTop;
    },

    /*
      发送网络请求
    */
    getHomeMultidata(){
      getHomeMultidata().then(res => {
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    })
    },
    getHomeGoods(type){
      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then(res => {
        this.goods[type].list.push(...res.data.data.list)
        this.goods[type].page += 1

        this.$refs.scroll.finishPullUp()
      })
    }

  },

  created() {
    this.getHomeMultidata()
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')


  },
  mounted(){
    //参数是函数是不需要在函数名后加()，加()是返回值
    //1.图片加载完成的事件监听
    const refresh = debounce(this.$refs.scroll.refresh,100)

    this.$bus.$on("itemImageLoad",() =>{
      refresh()
    })
  },

  activated(){
    this.$refs.scroll.scrollTo(0, this.saveY,0)
    this.$refs.scroll.refresh()
  },
  deactivated(){
    this.saveY = this.$refs.scroll.getScrollY()
  },
}

</script>
<style scoped>
  #home{
    padding-top: 49px;
    height: 100vh;
    position: relative;
  }

  .home-nav{
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    top: 0px;
    right: 0px;
    left: 0px;
    z-index: 5;
  }
  .content{
    overflow: hidden;
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  .tab-control{
    position: relative;
    z-index: 9;
  }
</style>
