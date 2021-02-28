<!--  -->
<template>
  <div>
    <swiper class="detail-swiper">
      <swiper-item v-for="item in topImages">
        <img :src="item" alt="">
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
import {Swiper,SwiperItem} from 'components/common/swiper'
export default {
  name:'DetaSwiper',
  data () {
    return {
    };
  },
  props:{
    topImages: {
      type: Array,
      default(){
        return []
      }
    }
  },

  components: {
    Swiper,
    SwiperItem
  },

  computed: {},


  methods: {}
}

</script>
<style scoped>
  .detail-swiper{
    height: 300px;
  }
</style>
