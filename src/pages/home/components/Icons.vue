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
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {},
      icons: [
        {
          id: '000001',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        }, {
          id: '000002',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
          desc: '一日游'
        }, {
          id: '000003',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png',
          desc: '一日游'
        }, {
          id: '000004',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '一日游'
        }, {
          id: '000005',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        }, {
          id: '000006',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
          desc: '一日游'
        }, {
          id: '000007',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png',
          desc: '一日游'
        }, {
          id: '000008',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '一日游'
        }, {
          id: '000009',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        }, {
          id: '000010',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
          desc: '一日游'
        }, {
          id: '000011',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png',
          desc: '一日游'
        }, {
          id: '000012',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '一日游'
        }
      ]
    }
  },
  computed: {
    pages () {
      let pages = []
      this.icons.forEach((icon, index) => {
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
  .icons >>> .swiper-container
    overflow: hidden
    height: 0
    padding-bottom: 50%
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
