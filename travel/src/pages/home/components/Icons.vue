<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icom-img">
            <img class="icon-img-content" :src="item.imgUrl" alt />
            <p class="icon-desc">{{ item.desc }}</p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'Icons',
  props: {
    iconList: Array
  },
  // 计算属性 实现热门呢景点可以滑动的效果
  computed: {
    pages() {
      const pages = []
      this.iconList.forEach((item, index) => {
        //向下取值,page等于9/8 显示第二页
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
.icons>>>.swiper-container
  height: 0
  padding-bottom: 50%
  .icon
    position: relative
    float: left
    padding-bottom: 25%
    width: 25%
    height: 0
    .icom-img
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: 0.44rem /* 22/50 */
      box-sizing: border-box
      padding: 0.1rem
      .icon-img-content
        height: 100%
        display: block
        margin: 0 auto
  .icon-desc
    padding-top .2rem /* 10/50 */
    text-align: center
    overflow: hidden
    white-space: nowrap
    text-overflow: ellipsis
</style>
