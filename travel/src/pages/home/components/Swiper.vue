<template>
  <div class="swiper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of list" :key="item.id"
        ><img class="img" :src="item.imgUrl" alt=""
      /></swiper-slide>

      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
/* eslint-disable */

export default {
  name: 'homeSwiper',
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.swiper>>>.swiper-pagination-bullet-active
  background-color #fff
// 防抖动 高/宽 上面的代码是更改非当前组件的样式
.swiper
 width 100%
 height 0
 overflow hidden
 padding-bottom 30%
 .img
  width 100%
</style>
