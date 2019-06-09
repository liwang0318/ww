<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li
        class="item border-bottom"
        v-for="item of recommendList"
        :key="item.id"
      >
        <!-- <div class="item-img-wrapper"> -->
        <img :src="item.imgUrl" alt="" class="item-img" />
        <!-- </div> -->
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc">{{ item.desc }}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
  }
}
</script>

<style lang="stylus" scoped>
.recommend-title
  line-height .8rem /* 40/50 */
  background-color #eee
  text-indent .2rem
.item
  height 1.9rem
  padding 0.1rem
  // background-color red
  .item-img
    height 1.7rem
    width 1.7rem
    float left
  .item-info
    float left
    padding-left .2rem /* 10/50 */
    .item-title
      height .4rem /* 20/50 */
      font-weight 700
    .item-desc
      height .4rem /* 20/50 */
      color #ccc
    .item-button
      background #ff9300
      padding 0 .2rem
      border-radius .06rem
      color #ffff
      line-height .44rem
</style>
