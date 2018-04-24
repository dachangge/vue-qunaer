<template>
  <div class="icons">
    <swiper  :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="icon" v-for="icon in page" :key="icon.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="icon.imgUrl">
          </div>
          <p class="icon-desc">
            {{icon.desc}}
          </p>
        </div>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pages () {
      let pages = []
      this.list.forEach((icon, index) => {
        let page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(icon)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/mixins.styl";
  .icons >>> .swiper-pagination
    bottom: 0
  .icons >>> .swiper-container
    overflow: hidden
    height: 0
    padding-bottom: calc(50% + 0.3rem)
  .icons
    margin-top: .1rem
    .icon
      position: relative
      float: left
      width: 25%
      padding-bottom: 25%
      .icon-img
        text-align: center
        position: absolute
        padding: 0.1rem
        top: 0
        left: 0
        right: 0
        bottom: 0.44rem
        .icon-img-content
          height: 100%
      .icon-desc
        position: absolute;
        left: 0
        right: 0
        bottom: 0
        text-align: center
        height: 0.44rem;
        line-height: 0.44rem;
        ellipse()
</style>
