<!--  -->
<template>
  <div class="goods">
    <goods-list-item v-for = "item in goods" :goodsitem="item"></goods-list-item>

  </div>
</template>

<script>
import GoodsListItem from 'components/content/goods/GoodsListItem'

export default {
  name:'',
  data () {
    return {
    };
  },
  props:{
    goods:{
      type:Array,
      default(){
        return []
      }
    }
  },

  components: {
    GoodsListItem
  },

  computed: {},


  methods: {}
}

</script>
<style scoped>
 .goods{
   display: flex;
   flex-wrap: wrap;
   justify-content: space-around;
   padding: 2px;
 }
</style>
