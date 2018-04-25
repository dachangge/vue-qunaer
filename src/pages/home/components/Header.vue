<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      请输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
          {{city}}
          <span class="iconfont">&#xe6aa;</span>
      </div>
    </router-link>

  </div>
</template>
<script>
import {mapState} from 'vuex'
export default{
  name: 'HomeHeader',
  computed: {
    ...mapState({
      city: 'city'
    })
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/variables.styl'
  .header
    display:flex
    line-height: $headerHeight
    color: #fff
    background-color: $bgColor
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align: center
        font-size: .35rem
    .header-input
      flex: 1
      background-color: #fff
      margin-top: .12rem
      height: .64rem
      line-height: .64rem
      border-radius: .1rem
      color: #ccc
      padding-left: .2rem
    .header-right
      min-width: 1.04rem
      padding: 0 .1rem
      text-align: center
      color: #fff

</style>
