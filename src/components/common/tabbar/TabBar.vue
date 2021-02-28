<!--  -->
<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name:'TabBar',
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
  #tab-bar{
    display: flex;

    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;

    height: 49px;
    background-color: #f4f4f4;
    box-shadow: 0px -1px 10px rgba(100, 100, 100, 0.2);
  }
</style>
