<template>
    <div class="recommend">
      <div class="title">热销推荐</div>
      <ul>
        <li class="item border-bottom" v-for="item in list" :key="item.id">
          <img class="item-img" :src="item.imgUrl">
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}</p>
            <button class="item-button">查看详情</button>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
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
      height: 1.8rem
      display: flex
      .item-img
        width: 1.6rem
        height: 1.6rem
        padding: 0.1rem
      .item-info
        flex: 1
        padding: 0.1rem
        min-width: 0
        .item-title
          font-size: 0.32rem
          line-height: 0.6rem
          height: 0.6rem
          ellipse()
        .item-desc
          margin: .1rem 0
          color: #ccc
          ellipse()
        .item-button
          margin: .1rem 0
          background: #ff9800
          padding: 0 .2rem
          color: #fff
          border-radius: 0.06rem

</style>
