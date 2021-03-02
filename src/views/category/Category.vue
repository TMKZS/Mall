<!--  -->
<template>
  <div>

      <nav-bar class="nav-bar"><div slot="center">商品分类</div>  </nav-bar>
      <div class="flex-f">

          <ul class="ul-f flex-s">
            <li class="li-s"
            :class="{active:currentIndex === index}"
            v-for= '(item, index) in titles'
            @click="itemClick(index)">{{item}}</li>
          </ul>

        <div  class="flex-s">
          <h2>标题标题</h2>
          <h2>标题标题</h2>
          <h2>标题标题</h2>
          <h2>标题标题</h2>
          <h2>标题标题</h2>
          <h2>标题标题</h2>
        </div>

    </div>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'

import BScroll from 'better-scroll'

export default {
  name:'Category',
  data () {
    return {
      titles: ['上衣','裤子','裙子','内衣','女鞋','男友','包包','运动','配饰','美妆','个护','家居','百货','母婴','食品'],
      currentIndex: 0,
    };
  },

  mounted(){

  },


  components: {
    NavBar
  },

  computed: {

  },


  methods: {
    itemClick(index){
      this.currentIndex = index;

    }
  }
}

</script>
<style scoped>
  .nav-bar {
    background-color: var(--color-tint);
    color: #fff;
  }

  .li-s {
    background-color: #f6f6f6;
    /* border: 1px solid red; */
    width: 80px;
    height: 40px;
    line-height: 40px;
    text-align: center;
    font-size: 14px;
  }
  .active{
    background-color: #fff;
    border-left: 4px pink solid ;
  }

  .flex-f{
    display: flex;
  }

  .flex-s{
    flex: 1;
  }

</style>
