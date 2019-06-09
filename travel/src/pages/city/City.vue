<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="handlerChange"></city-alphabet>
  </div>
</template>

<script>
/* eslint-disable */
import axios from 'axios'
import cityHeader from './commponents/header.vue'
import citySearch from './commponents/search.vue'
import cityList from './commponents/list.vue'
import cityAlphabet from './commponents/Alphabet.vue'
export default {
  name: 'City',
  data() {
    return {
      cities: {},
      hotCities: [],
      letter: ''
    }
  },
  components: {
    cityHeader,
    citySearch,
    cityList,
    cityAlphabet
  },
  methods: {
    isCityRender() {
      axios.get('/api/city.json').then(res => {
        console.log(res)
        if (res.data.ret) {
          this.cities = res.data.data.cities
          this.hotCities = res.data.data.hotCities
        }
      })
    },
    handlerChange(letter) {
      this.letter = letter
    }
  },
  mounted() {
    this.isCityRender()
  }
}
</script>

<style lang="stylus" scoped></style>
