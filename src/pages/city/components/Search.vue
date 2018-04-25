<template>
  <div>
    <div class="search">
      <input type="text" v-model="keyWord" class="search-input" placeholder="请输入城市名或拼音">
    </div>
    <div class="search-connent" ref="searchContent" v-show="keyWord" >
      <ul>
        <li class="search-item border-bottom" v-for="item in list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="notFind">未找到符合条件的数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import {mapMutations} from 'vuex'
import BScroll from 'better-scroll'
export default {
  props: {
    cities: Object
  },
  data () {
    return {
      keyWord: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (cityname) {
      this.changeCity(cityname)
      this.$router.push({path: '/'})
    },
    ...mapMutations(['changeCity'])
  },
  name: 'CitySearch',
  mounted () {
    this.scroll = new BScroll(this.$refs.searchContent)
  },
  computed: {
    notFind () {
      return !this.list.length
    }
  },
  watch: {
    keyWord () {
      this.list = []
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        for (let key in this.cities) {
          this.cities[key].forEach((it) => {
            if (it.spell.indexOf(this.keyWord) >= 0 || it.name.indexOf(this.keyWord) >= 0) {
              this.list.push(it)
            }
          })
        }
      }, 100)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/variables.styl'
  .search
    height: 0.72rem
    padding: .1rem
    background: $bgColor
    .search-input
      box-sizing: border-box
      padding: 0 .1rem
      width: 100%
      height: .62rem
      line-height: .62rem
      text-align: center
      border-radius: .06rem
  .search-connent
    position: absolute
    top: 1.72rem
    left: 0
    right: 0
    bottom: 0
    background: #ccc
    z-index: 1
    overflow: hidden
    .search-item
      height: 0.64rem
      line-height: 0.64rem
      padding-left: .2rem
      color: #000
      background: #fff

</style>
