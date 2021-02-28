<!--  -->
<template>
  <div>
    <nav-bar>
      <div slot="left" class="back" @click="backClick"><img src="~assets/img/common/back.svg" alt=""></div>
      <div slot="center" class="titles">
        <div v-for="(item,index) in titles"
        class="titles-item"
        :class="{active: index === currentIndex}"
        @click = "itemClick(index)">{{item}}</div>
      </div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
export default {
  name:'DetaNavBar',
  data () {
    return {
      titles: ['商品','参数','评论','推荐'],
      currentIndex: 0
    };
  },

  components: {
    NavBar
  },

  computed: {},


  methods: {
    itemClick(index){
      this.currentIndex = index,
      this.$emit("titleClick",index)
    },
    backClick(){
      this.$router.back()
    }
  }
}

</script>
<style scoped>
  .titles{
    display: flex;
  }
  .titles-item{
    flex: 1
  }
  .active{
    color: var(--color-high-text);
  }
  .back{
    margin-top: 5px;
    margin-left: 10px;
  }
</style>
