<template>
  <div>
    <home-header ></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekday :list="weekdayList"></home-weekday>
  </div>
</template>

<script>
import HomeSwiper from './components/Swiper.vue'
import HomeHeader from './components/Header.vue'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekday from './components/Weekday'
import axios from 'axios'
import {mapState} from 'vuex'
export default{
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekday
  },
  data () {
    return {
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekdayList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('api/index.json?city=' + this.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      if (res.data.ret && res.data.data) {
        let data = res.data.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekdayList = data.weekdayList
      }
    }
  },
  computed: {
    ...mapState(['city'])
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.city !== this.lastCity) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style scoped>

</style>
