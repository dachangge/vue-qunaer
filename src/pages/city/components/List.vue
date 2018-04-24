<template>
    <div class="list" ref="wrapper">
      <div >
        <div class="arear">
          <div class="list-title border-topbottom">当前城市</div>
          <div class="button-list">
            <div class="button-warpper">
              <div class="button">北京</div>
            </div>
          </div>
        </div>
        <div class="area">
          <div class="list-title border-topbottom">热门城市</div>
          <div class="button-list">
            <div class="button-warpper" v-for="city in hotCities" :key="city.id">
              <div class="button">{{city.name}}</div>
            </div>
          </div>
        </div>
        <div class="area" v-for="(city,key) in cities" :key="key">
          <div class="list-title border-topbottom">{{key}}</div>
          <ul class="item-list">
            <li class="item border-bottom" v-for="innercity in city" :key="innercity.id">{{innercity.name}}</li>
          </ul>
        </div>
      </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: Array
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/variables.styl";
  .list
    position: absolute
    top: 1.72rem
    left: 0
    right: 0
    bottom: 0
    overflow: hidden
    .list-title
      height: 0.54rem
      line-height: 0.54rem
      background: #ccc
      color: #666
      font-size: .25rem
      padding-left: .2rem
      &:before
        border-color: #666
      &:after
        border-color: #666
    .button-list
       overflow: hidden
       padding-right: .6rem
       .button-warpper
        width: 33.3%
        float: left;
        .button
          margin: .1rem
          text-align: center
          border: .02rem solid #ccc
          padding: .1rem 0
          border-radius: .06rem
    .item-list
      .item
        line-height: 0.64rem
        padding-left: 0.2rem
        &:before
         border-color: #ccc
</style>
