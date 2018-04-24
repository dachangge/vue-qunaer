<template>
  <div class="cityHeader">
    选择城市
    <router-link to="/">
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import "~styles/variables.styl";
  .cityHeader
    line-height: $headerHeight
    height: $headerHeight
    background: $bgColor
    font-size: .32rem
    color: #fff
    position: relative
    text-align: center
    .back-icon
      position: absolute
      top: 0
      left: 0
      line-height: $bgColor
      color: #fff
      width: 0.64rem
      text-align: center

</style>
