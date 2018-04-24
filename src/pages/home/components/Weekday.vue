<template>
  <div class="recommend">
    <div class="title">周末去哪玩</div>
    <ul>
      <li class="item border-bottom" v-for="item in list" :key="item.id">
        <div class="item-img-wapper">
          <img class="item-img" :src="item.imgUrl">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekDay',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl";
  .recommend
    margin-top: .2rem
    .title
      line-height: 0.9rem
      height: 0.9rem
      background: #ccc
      text-indent: 0.2rem
    .item
      height: 4.4rem
      .item-img-wapper
        height: 0
        padding-bottom: 37.1%
        overflow: hidden
        .item-img
          width: 100%
      .item-info
        padding: 0.1rem
        min-width: 0
      .item-title
        line-height: 0.48rem
        height: 0.48rem
        color: #212121
        ellipse()
      .item-desc
        margin: .1rem 0
        color: #616161
        ellipse()
      .item-button
        margin: .1rem 0
        background: #ff9800
        padding: 0 .2rem
        border-radius: 0.06rem

</style>
