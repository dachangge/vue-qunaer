<template>
    <div class="alphabet">
      <ul class="item-list" >
        <div class="item" v-for="(item,key) in cities"
             :key="key"
             @click="handLetterClick"
             @touchstart="handleTouchStart"
             @touchmove="handleTouchMove"
             @touchend="handleTouchEnd"
             :ref="key"
        >
          {{key}}
        </div>
      </ul>
    </div>
</template>

<script>
export default {
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      fontSize: 0,
      firstHeight: 0,
      timer: null
    }
  },
  updated () {
    let str = window.getComputedStyle(document.documentElement)['font-size']
    this.fontSize = +str.substr(0, str.length - 2)
    this.firstHeight = this.$refs['A'][0].offsetTop
  },
  methods: {
    handLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          let index = Math.floor((e.touches[0].clientY - this.fontSize * 1.72 - this.firstHeight) / (this.fontSize * 0.4))
          this.$emit('change', this.trueArr[index])
        }, 20)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  },
  name: 'CityAlphabet',
  computed: {
    trueArr () {
      let arr = []
      for (let key in this.cities) {
        arr.push(key)
      }
      return arr
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/variables.styl";
  .alphabet
    position: absolute
    top: 1.72rem
    right: 0
    bottom: 0
    width: .4rem
    display: flex
    justify-content: center
    align-items: center
    .item-list
      .item
        text-align: center
        line-height: .4rem
        color: $bgColor
</style>
