<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item of WeekendList" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" alt="" class="item-img" />
        </div>
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc">{{ item.desc }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'HomeWeekend',
  props: {
    WeekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
.recommend-title
  line-height .8rem /* 40/50 */
  background-color #eee
  text-indent .2rem
.item-img-wrapper
  overflow hidden
  height 0
  padding-bottom 37.09%
  .item-img
    height 2.8rem /* 140/50 */
    width 100%
.item-info
  height 1rem /* 50/50 */
  padding-top .2rem /* 10/50 */s
  .item-title
    line-height .4rem /* 20/50 */
    font-weight 700
  .item-desc
    line-height .6rem /* 30/50 */
    color #cccs
</style>
