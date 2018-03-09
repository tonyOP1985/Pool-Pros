<template>
  <div id="app">
    <TopHeader></TopHeader>
    <NavBar v-bind:windowWidth="windowWidth"></NavBar>
    <Jumbotron></Jumbotron>
    <Directions></Directions>
    <FilterResults v-bind:windowWidth="windowWidth"></FilterResults>
    <FilterResultsLarge v-bind:windowWidth="windowWidth"></FilterResultsLarge>
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

export default {
  name: 'App',
  components: {
    NavBar,
    Jumbotron,
    Directions,
    TopHeader,
    SiteFooter,
    FilterResults,
    FilterResultsLarge
  },
  data () {
    return {
      windowWidth: 0
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
  }
</style>
