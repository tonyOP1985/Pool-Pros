<template>
  <div id="app" :class="{ hideScrollBar: hideScroll }">
    <TopHeader></TopHeader>
    <NavBar :windowWidth="windowWidth" @getProDealers="sendDealers" @openSideNav="hideScrollBar"></NavBar>
    <Jumbotron></Jumbotron>
    <Directions></Directions>
    <div class="filter-mobile" v-show="dealers.length">
      <FilterResults :dealers="dealers" :windowWidth="windowWidth"></FilterResults>
    </div>
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
    // Dealers
  },
  data () {
    return {
      windowWidth: 0,
      dealers: {},
      hideScroll: false
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
    },
    hideScrollBar (bool) {
      this.hideScroll = bool
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
    position: relative;
    flex: 1;
  }

  .filter-large {
    height: 12rem;
  }

  .hideScrollBar {
    overflow: hidden;
    height: 100%;
    position: fixed;
  }
</style>
