<!--  -->
<template>
  <div class="nav-bar">
    <div class="left"><slot name="left"></slot></div>
    <div class="center"><slot name="center"></slot></div>
    <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
export default {
  name:'NavBar',
  data () {
    return {
    };
  },

  components: {},

  computed: {},


  methods: {}
}

</script>
<style scoped>
  .nav-bar{
    display: flex;
    line-height: 49px;
  }
  .left , .right{
    width: 44px;
  }
  .center{
    flex: 1;
    text-align:center;
  }
</style>
