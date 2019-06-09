<template>
  <div>
    <div class="search">
      <input v-model="keyword" type="text" placeholder="输入城市名或拼音" class="city-search">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li
          class="search-item border-bottom"
          v-for="item of list"
          :key="item.id"
          @click="handlerChange(item.name)"
        >{{ item.name }}</li>
        <li class="search-item border-bottom" v-show="!list.length">没有更多数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
//页面滚动
import Bscroll from 'better-scroll'
export default {
  name: 'citySearch',
  //接收city.vue的数据
  props: {
    cities: Object
  },
  data() {
    return {
      //双向绑定
      keyword: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handlerChange(city) {
      this.$store.commit('changeCity', city)
      this.$router.push('/')
    }
  },
  watch: {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (
              value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1
            ) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
.search
  // line-height: 0.86rem
  background-color: #00bcd4
  height: 0.76rem
  padding: 0 0.1rem /* 5/50 */
  .city-search
    box-sizing: border-box
    width: 100%
    height: 0.6rem
    line-height: 0.6rem
    border-radius: 0.1rem /* 5/50 */
    text-align: center
    color: #666
    padding: 0 0.02rem /* 1/50 */
.search-content
  z-index: 1
  overflow: hidden
  position: absolute
  top: 1.58rem
  left: 0
  right: 0
  bottom: 0
  // background: red
  .search-item
    line-height: 0.62rem
    padding-left: 0.2rem
    color: #666
    background: #fff
</style>
