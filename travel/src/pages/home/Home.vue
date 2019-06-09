<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <icons :iconList="iconList"></icons>
    <home-recommend :recommendList="recommendList"></home-recommend>
    <home-weekend :WeekendList="WeekendList"></home-weekend>
  </div>
</template>

<script>
/* eslint-disable */
import homeHeader from './components/header/header.vue'
import homeSwiper from './components/Swiper.vue'
import Icons from './components/Icons.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import axios from 'axios'

export default {
  name: 'Home',
  data() {
    return {
      swiperList: [],
      recommendList: [],
      iconList: [],
      WeekendList: []
    }
  },
  components: {
    homeHeader,
    homeSwiper,
    Icons,
    HomeRecommend,
    HomeWeekend
  },
  mounted() {
    this.homerender()
  },

  methods: {
    homerender() {
      axios.get('/api/index.json').then(res => {
        console.log(res)
        if (res.data.ret) {
          this.swiperList = res.data.data.swiperList
          this.recommendList = res.data.data.recommendList
          this.iconList = res.data.data.iconList
          this.WeekendList = res.data.data.WeekendList
        }
      })
    }
  }
}
</script>

<style></style>
