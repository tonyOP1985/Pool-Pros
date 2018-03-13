<template>
  <div id="app">
    <TopHeader></TopHeader>
    <NavBar :windowWidth="windowWidth" @getProDealers="sendDealers"></NavBar>
    <Jumbotron></Jumbotron>
    <Directions :dealers="dealers"></Directions>
    <div class="filter-mobile" v-show="dealers.length">
      <FilterResults :dealers="dealers" :windowWidth="windowWidth"></FilterResults>
    </div>
    <!-- <div class="filter-large" v-show="windowWidth >= 768 && dealers.length">
      <FilterResultsLarge :dealers="dealers"></FilterResultsLarge>
    </div> -->
    <Dealers :dealers="dealers"></Dealers>
    <SiteFooter></SiteFooter>
  </div>
</template>

<script>
import TopHeader from './components/TopHeader.vue'
import NavBar from './components/NavBar.vue'
import Jumbotron from './components/Jumbotron.vue'
import Directions from './components/Directions.vue'
import SiteFooter from './components/SiteFooter.vue'
import FilterResults from './components/FilterResults.vue'
import FilterResultsLarge from './components/FilterResultsLarge.vue'
import Dealers from './components/Dealers.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    Jumbotron,
    Directions,
    TopHeader,
    SiteFooter,
    FilterResults,
    FilterResultsLarge,
    Dealers
  },
  data () {
    return {
      windowWidth: 0,
      dealers: {}
    }
  },
  mounted () {
    this.$nextTick(() => {
      window.addEventListener('resize', this.getWindowWidth)

      this.getWindowWidth()
    })
  },
  methods: {
    getWindowWidth () {
      this.windowWidth = document.documentElement.clientWidth
    },
    openSideNav () {
      this.isOpen = !this.isOpen
    },
    sendDealers (pros) {
      this.dealers = pros
      console.log(this.dealers)
    }
  },
  beforeDestroy () {
    window.addEventListener('resize', this.getWindowWidth)
  }
}
</script>

<style lang="scss">
  @import "assets/app.scss";
  #app {
    width: 100%;
    overflow: hidden;
  }

  .filter-large {
    height: 12rem;
  }
</style>
