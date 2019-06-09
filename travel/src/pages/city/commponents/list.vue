<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{ this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hotCities" :key="item.id">
            <div class="button" @click="handlerChange(item.name)">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{ key }}</div>
        <div class="item-list">
          <div
            class="item border-bottom"
            v-for="ite of item"
            :key="ite.id"
            @click="handlerChange(ite.name)"
          >{{ ite.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import Bscroll from 'better-scroll'
export default {
  name: 'cityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  methods: {
    handlerChange(city) {
      this.$store.commit('changeCity', city)
      this.$router.push('/')
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter() {
      if (this.letter) {
        console.log(this.letter)
        const e = this.$refs[this.letter][0]
        this.scroll.scrollToElement(e)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.border-topbottom
  &:before
    border-color: #ccc
  &:after
    border-color: #ccc
.border-bottom
  &:before
    border-color: #ccc
  &:after
    border-color: #ccc
.list
  overflow: hidden
  position: absolute
  top: 1.58rem
  left: 0
  right: 0
  bottom: 0
  .title
    line-height: 0.54rem
    background: #eee
    padding-left: 0.2rem /* 10/50 */
    color: #666
    font-size: 0.26rem
  .button-list
    overflow: hidden
    padding: 0.1rem
    .button-wrapper
      float: left
      width: 33.33%
      .button
        margin: 0.1rem
        padding: 0.1rem 0
        text-align: center
        border: 0.02rem /* 1/50 */ solid #ccc
        border-radius: 0.1rem /* 5/50 */
  .item-list
    .item
      line-height: 0.76rem
      padding-left: 0.2rem
</style>
