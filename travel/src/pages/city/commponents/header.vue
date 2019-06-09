<template>
  <div class="header">
    <router-link to="/">
      <span class="iconfont city-left">&#xe624;</span>
    </router-link>
    <span class="city-center">城市选择</span>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'cityHeader'
}
</script>

<style lang="stylus" scoped>
.header
  // line-height: 0.86rem
  background-color: #00bcd4
  height: 0.86rem
  .city-left
    position: relative
    left: 0.2rem /* 10/50 */
    top: 0.3rem /* 15/50 */
    color: #fff
    line-height: 0.2rem
  .city-center
    position: absolute
    display: block
    width: 100%
    line-height: 0.3rem
    font-size: 0.32rem /* 16/50 */
    text-align: center
    color: #fff
</style>
