<!--  -->
<template>
  <div class="recommend">
    <div v-for="item in recommends" class="recommend-item">
      <a :href="item.link">
      <img :src="item.image" alt="">
      <div>{{item.title}}</div>
    </a>
    </div>
  </div>
</template>

<script>
export default {
  name:'RecommendView',
  data () {
    return {
    };
  },
  props:{
    recommends:{
      type:Array,
      default(){
        return []
      }
    }
  },

  components: {},

  computed: {},


  methods: {}
}

</script>
<style scoped>
  .recommend{
    display: flex;
    text-align: center;
    padding: 10px 0 20px;
    border-bottom: 10px solid #eee;
  }

  .recommend-item{
    flex:1;
    font-size: 14px;
  }

  .recommend-item img{
    height: 65px;
    width: 65px;
    margin-bottom: 10px;

  }
</style>
