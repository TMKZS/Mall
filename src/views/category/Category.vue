<!--  -->
<template>
  <div class="wrapper">
    <ul class="content">
      <li>分类商品1</li>
      <li>分类商品2</li>
      <li>分类商品3</li>
      <li>分类商品4</li>
      <li>分类商品5</li>
      <li>分类商品6</li>
      <li>分类商品7</li>
      <li>分类商品8</li>
      <li>分类商品9</li>
      <li>分类商品10</li>
      <li>分类商品11</li>
      <li>分类商品12</li>
      <li>分类商品13</li>
      <li>分类商品14</li>
      <li>分类商品15</li>
      <li>分类商品16</li>
      <li>分类商品17</li>
      <li>分类商品18</li>
      <li>分类商品19</li>
      <li>分类商品20</li>
      <li>分类商品21</li>
      <li>分类商品22</li>
      <li>分类商品23</li>
      <li>分类商品24</li>
      <li>分类商品25</li>
      <li>分类商品26</li>
      <li>分类商品27</li>
      <li>分类商品28</li>
      <li>分类商品29</li>
      <li>分类商品30</li>
      <li>分类商品31</li>
      <li>分类商品32</li>
      <li>分类商品33</li>
      <li>分类商品34</li>
      <li>分类商品35</li>
      <li>分类商品36</li>
      <li>分类商品37</li>
      <li>分类商品38</li>
      <li>分类商品39</li>
      <li>分类商品40</li>
      <li>分类商品41</li>
      <li>分类商品42</li>
      <li>分类商品43</li>
      <li>分类商品44</li>
      <li>分类商品45</li>
      <li>分类商品46</li>
      <li>分类商品47</li>
      <li>分类商品48</li>
      <li>分类商品49</li>
      <li>分类商品50</li>
      <li>分类商品51</li>
      <li>分类商品52</li>
      <li>分类商品53</li>
      <li>分类商品54</li>
      <li>分类商品55</li>
      <li>分类商品56</li>
      <li>分类商品57</li>
      <li>分类商品58</li>
      <li>分类商品59</li>
      <li>分类商品60</li>
      <li>分类商品61</li>
      <li>分类商品62</li>
      <li>分类商品63</li>
      <li>分类商品64</li>
      <li>分类商品65</li>
      <li>分类商品66</li>
      <li>分类商品67</li>
      <li>分类商品68</li>
      <li>分类商品69</li>
      <li>分类商品70</li>
      <li>分类商品71</li>
      <li>分类商品72</li>
      <li>分类商品73</li>
      <li>分类商品74</li>
      <li>分类商品75</li>
      <li>分类商品76</li>
      <li>分类商品77</li>
      <li>分类商品78</li>
      <li>分类商品79</li>
      <li>分类商品80</li>
      <li>分类商品81</li>
      <li>分类商品82</li>
      <li>分类商品83</li>
      <li>分类商品84</li>
      <li>分类商品85</li>
      <li>分类商品86</li>
      <li>分类商品87</li>
      <li>分类商品88</li>
      <li>分类商品89</li>
      <li>分类商品90</li>
      <li>分类商品91</li>
      <li>分类商品92</li>
      <li>分类商品93</li>
      <li>分类商品94</li>
      <li>分类商品95</li>
      <li>分类商品96</li>
      <li>分类商品97</li>
      <li>分类商品98</li>
      <li>分类商品99</li>
      <li>分类商品100</li>
    </ul>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name:'Category',
  data () {
    return {
      scroll : null,
    };
  },

  mounted(){
    this.scroll = new BScroll(document.querySelector('.wrapper'),{

    })
  },


  components: {},

  computed: {},


  methods: {}
}

</script>
<style scoped>
  .wrapper{
    height: 150px;
    background-color: red;
  }
</style>
