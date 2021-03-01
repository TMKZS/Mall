<!--  -->
<template>
  <div id="profile">
    <nav-bar class="profile-nav">
      <div slot="center">我的</div>
    </nav-bar>
    <user-info></user-info>
    <section class="account">
      <div class="account-item">
        <div class="number">
          <span class="balance">0.00</span>元
        </div>
        <div class="account-info">我的余额</div>
      </div>

      <div class="account-item">
        <div class="number">
          <span class="balance">0</span>个
        </div>
        <div class="account-info">我的优惠</div>
      </div>

      <div class="account-item">
        <div class="number">
          <span class="balance">0</span>分
        </div>
        <div class="account-info">我的积分</div>
      </div>
    </section>

    <div class="backg-top backg-bottom">
      我的消息
    </div>
    <div class="backg-bottom">
      积分商城
    </div>
    <div class="backg-bottom">
      会员卡
    </div>

    <div class="bottom backg-bottom">
      我的购物车
    </div>
    <div class="backg-bottom">
      下载购物APP
    </div>

    <div></div>
  </div>
</template>

<script>
 import NavBar from 'components/common/navbar/NavBar'
 import UserInfo from './childComps/UserInfo'
export default {
  name:'Profile',
  data () {
    return {
    };
  },

  components: {
    NavBar,
    UserInfo
  },

  computed: {},


  methods: {}
}

</script>
<style scoped>
  #profile{
    background-color: #f2f2f2;
  }

  .profile-nav {
    background-color: var(--color-tint);
    color: #fff;
  }

  .account{
    display: flex;
    margin-bottom: 10px;

  }

  .account-item{
    flex: 1;
    text-align: center;

    color: #666;
    font-size: 14px;
    padding: 18px;

    background-color: #fff;
    margin-right: 1px;
  }
  .balance{
    font-size: 24px;
    color: #f00;
  }
  .backg-top{
    margin-top: 20px;
  }
  .backg-bottom{
    background-color: #fff;
    height: 44px;
    line-height: 44px;
    /* padding-bottom: 10px; */
    padding-left: 60px;
    margin-bottom: 5px;
  }
  .bottom{
    margin-top: 20px;
  }
</style>
