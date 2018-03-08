<template>
  <div id="app">
    <TopHeader></TopHeader>
    <NavBar></NavBar>
    <Jumbotron></Jumbotron>
    <Directions></Directions>
    <!-- <filter-results></filter-results> -->
    <FilterResults></FilterResults>
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

export default {
  name: 'App',
  components: {
    NavBar,
    Jumbotron,
    Directions,
    TopHeader,
    SiteFooter,
    FilterResults
  }
}
</script>

<style lang="scss">
  @import "assets/app.scss";
  #app {
    width: 100%;
  }
</style>
