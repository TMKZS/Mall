<!--  -->
<template>
  <div id="detail" >
    <deta-nav-bar class="detail-nav" @titleClick="titleClick" ref = "nav"/>
    <scroll class="content" ref='scroll' :probe-type="3" @scroll="contentScroll">
      <detail-swiper :top-images= "topImages"/>
      <detail-base-info :goods="goods"/>
      <detail-shop-info :shop="shop"/>
      <detail-goods-info :detail-info="detailIfon" @imageLoad='imageLoad'/>
      <detail-param-info ref="params" :param-info="paramInfo"/>
      <detail-comment-info ref="comment" :comment-info="commentInfo"/>
      <goods-list ref="recommend" :goods="recommends"/>
    </scroll>
    <detail-bottom-bar @addToCart ="addToCart"/>
  </div>
</template>

<script>
import DetaNavBar from './childComps/DetailNavBar'
import DetailSwiper from './childComps/DetailSwiper'
import DetailBaseInfo from './childComps/DetailBaseInfo'
import DetailShopInfo from './childComps/DetailShopInfo'
import DetailGoodsInfo from './childComps/DetailGoodsInfo'
import DetailParamInfo from './childComps/DetailParamInfo'
import DetailCommentInfo from './childComps/DetailCommentInfo'
import DetailBottomBar from './childComps/DetailBottomBar'


import Scroll from 'components/common/scroll/Scroll'
import GoodsList from 'components/content/goods/GoodsList'


import {getDetail, Goods, GoodsParam, Shop,getRecommend} from 'network/detail'
import { debounce } from 'common/utils'
import { mapActions } from 'vuex'

export default {
  name:'Detail',
  data () {
    return {
      iid: null,
      topImages: [],
      goods: {},
      shop: {},
      detailIfon: {},
      paramInfo: {},
      commentInfo: {},
      recommends: [],
      themeTopYs: [],
      currentIndex: 0,

    };
  },

  components: {
    DetaNavBar,
    DetailSwiper,
    DetailBaseInfo,
    DetailShopInfo,
    DetailGoodsInfo,
    DetailParamInfo,
    DetailCommentInfo,
    GoodsList,
    DetailBottomBar,

    Scroll
  },

  computed: {},
  created(){
    //1.保存传入的iid
    this.iid = this.$route.params.iid
    //2.根据iid请求详情数据
    getDetail(this.iid).then(res =>{
      //1.获取轮播图信息
      // console.log(res);
      const data = res.data.result
      this.topImages = data.itemInfo.topImages
      //2.获取商品信息
      this.goods = new Goods(data.itemInfo,data.columns,data.shopInfo.services)
      //3.创建店铺信息的对象
      this.shop = new Shop(data.shopInfo)
      //4.保存商品数据的详情数据
      this.detailIfon = data.detailInfo
      //5.获取参数信息
      this.paramInfo = new GoodsParam(data.itemParams.info,data.itemParams.rule)
      //6.取出评论信息
      if(data.rate.cRate !== 0){
        this.commentInfo = data.rate.list[0]
      }
    })
    getRecommend().then(res => {
      console.log(res)
      this.recommends = res.data.data.list
    })
    this.themeTopYs = debounce(() => {
      this.themeTopYs = [],
      // this.themeTopYs = this.$refs.params.$el.offsetTop
      this.themeTopYs.push(0)
      this.themeTopYs.push(this.$refs.params.$el.offsetTop)
      this.themeTopYs.push(this.$refs.comment.$el.offsetTop)
      this.themeTopYs.push(this.$refs.recommend.$el.offsetTop)
      // console.log(this.themeTopYs)
    },500)

  },

  contentStroll(position){
      this.isShowBackTop = (-position.y) > 1000;
    },


  methods: {
    ...mapActions(['addCart']),


    imageLoad(){
      this.$refs.scroll.refresh()

      this.themeTopYs()
    },
    addToCart(){
        const product = {};
        product.imge = this.topImages[0];
        product.title = this.goods.title;
        product.desc = this.goods.desc;
        product.price = this.goods.realPrice;
        product.iid = this.iid;

        // this.$store.commit("addCart",product)

        this.addCart(product).then(res => {
          console.log(res)
        })

        // this.$store.dispatch('addCart',product).then(res => {
        //   console.log(res);
        // })
    },

    titleClick(index){
      // console.log(index);
      this.$refs.scroll.scrollTo(0, -this.themeTopYs[index], 200)
    },

    contentScroll(position){
      //获取Y值
      const positionY = -position.y
      let length = this.themeTopYs.length
      for (let i = 0; i < length; i++) {
        // if( (i < length-1 ) && ((positionY > this.themeTopYs[i]) && (positionY < this.themeTopYs[i+1])||(i === length-1 && positionY >this.themeTopYs[i]))){
        //   console.log(i)
        // }
        if(this.currentIndex !== i &&(( i < length-1 && positionY >= this.themeTopYs[i]&& positionY <this.themeTopYs[i+1]) || (i === length - 1 && positionY >= this.themeTopYs[i]))){
          this.currentIndex = i ;
          // console.log(this.currentIndex);
          this.$refs.nav.currentIndex = this.currentIndex
        }
      }
    }
  }
}

</script>
<style scoped>
  #detail{
    position: relative;
    z-index:9;
    background-color: #fff;
    height: 100vh;
  }

  .detail-nav{
    position: relative;
    z-index: 9;
    background-color: #fff;
  }

  .content{
    height: calc(100% - 44px - 58px);
  }
</style>
