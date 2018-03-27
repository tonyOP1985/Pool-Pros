<template>
  <div id="app" class="app" :class="{ hideScrollBar: hideScroll }" v-cloak>
    <header>
      <TopHeader></TopHeader>
      <NavBar :windowWidth="windowWidth" @getProDealers="sendDealers" @openSideNav="hideScrollBar"></NavBar>
    </header>
    <div class="content">
      <Jumbotron></Jumbotron>
      <Directions></Directions>
      <div class="filter-mobile" v-show="dealers.length">
        <FilterResults :dealers="dealers" :windowWidth="windowWidth"></FilterResults>
      </div>
    </div>
    <footer>
      <SiteFooter></SiteFooter>
    </footer>
  </div>
</template>

<script>
import TopHeader from './components/TopHeader.vue'
import NavBar from './components/NavBar.vue'
import Jumbotron from './components/Jumbotron.vue'
import Directions from './components/Directions.vue'
import SiteFooter from './components/SiteFooter.vue'
import FilterResults from './components/FilterResults.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    Jumbotron,
    Directions,
    TopHeader,
    SiteFooter,
    FilterResults
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

<style lang="scss" scoped>
  @import "assets/app.scss";
  .app {
    width: 100%;
    min-height: 100%;
    display: flex;
    flex-direction: column;
    align-items: stretch;
    position: relative;
  }

  [v-cloak] {
    display: none;
  }

  .content {
    flex-grow: 1;
  }

  header, .content, footer {
    flex-shrink: 0;
  }

  .hideScrollBar {
    position: fixed;
  }
</style>
