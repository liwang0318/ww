<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{ this.$store.state.city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'homeHeader'
}
</script>

<style lang="stylus" scoped>
.header
  line-height: 0.86rem
  background-color: #00bcd4
  display: flex
  color: #fff
  .header-left
    width: 0.64rem
    float: left
    text-align: center
    font-size: 0.48rem /* 24/50 */
  .header-input
    flex: 1
    height: 0.64rem
    line-height: 0.64rem
    background-color: #fff
    margin-top: 0.12rem
    margin-left: 0.2rem
    border-radius: 0.1rem /* 5/50 */
    color: #ccc
    padding-left: 0.2rem /* 10/50 */
  .header-right
    width: 1.24rem
    float: right
    text-align: center
    color: #fff
  .arrow-icon
    font-size: 0.24rem /* 12/50 */
    margin-left: -0.1rem
</style>
