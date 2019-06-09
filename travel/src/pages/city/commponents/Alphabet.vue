<template>
  <ul class="list">
    <li
      class="item"
      v-for="item of letters"
      :key="item"
      :ref="item"
      @touchstart="handlerStart"
      @touchmove="handlerMove"
      @touchend="handlerEnd"
      @click="handleClick"
    >{{ item }}</li>
  </ul>
</template>

<script>
/* eslint-disable */
export default {
  name: 'cityAlphabet',
  data() {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated() {
    this.startY = this.$refs['A'][0].offsetTop
  },
  //计算属性
  computed: {
    letters() {
      //声明一个数组,把ABC添加到数组中
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  props: {
    cities: Object
  },

  methods: {
    handleClick(e) {
      // console.log(e.target.innerText)
      this.$emit('change', e.target.innerText)
    },
    handlerStart() {
      this.touchStatus = true
    },
    handlerMove(e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          // const startY = this.$refs['A'][0].offsetTop

          const touchY = e.touches[0].clientY - 79
          console.log(touchY)
          const index = Math.floor((touchY - this.startY) / 20)
          console.log(index)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handlerEnd() {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
.list
  display: flex
  flex-direction: column
  justify-content: center
  position: absolute
  top: 1.58rem
  right: 0
  bottom: 0
  width: 0.3rem
  .item
    text-align: center
    line-height: 0.4rem
    color: #00bcd4
</style>
