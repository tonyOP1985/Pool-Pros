<template>
  <div id="app" class="app" :class="{ hideScrollBar: hideScroll }">
    <header>
      <TopHeader></TopHeader>
      <NavBar1 :windowWidth="windowWidth" @getProDealers="sendDealers" @openSideNav="hideScrollBar"></NavBar1>
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
import NavBar1 from './components/NavBar1.vue'
import Jumbotron from './components/Jumbotron.vue'
import Directions from './components/Directions.vue'
import SiteFooter from './components/SiteFooter.vue'
import FilterResults from './components/FilterResults.vue'

export default {
  name: 'App',
  components: {
    NavBar1,
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

  .content {
    flex-grow: 1;
  }

  header, .content, footer {
    flex-shrink: 0;
  }

  // .filter-large {
  //   height: 12rem;
  // }

  .hideScrollBar {
    position: fixed;
  }
</style>
