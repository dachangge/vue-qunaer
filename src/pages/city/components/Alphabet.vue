<template>
    <div class="alphabet">
      <ul class="item-list">
        <div class="item">A</div>
        <div class="item">A</div>
        <div class="item">A</div>
        <div class="item">A</div>
        <div class="item">A</div>
        <div class="item">A</div>
        <div class="item">A</div>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'CityAlphabet'
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
