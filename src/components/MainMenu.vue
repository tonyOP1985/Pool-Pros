<template>
  <div class="menu">
    <div class="container">
      <div class="menu-wrapper">
        <!-- <div class="menu__logo">
          <a href="#">
            <img src="static/img/pool-pros-logo.png" alt="Pool Pros" title="POOL PROS">
          </a>
        </div> -->
        <!-- <NavBar></NavBar> -->
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from './NavBar.vue'

export default {
  name: 'mainMenu',
  components: {
    NavBar
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .menu {
    width: 100%;
    height: 5rem;
    font-family: $text-primary;

    @include center-vertical;
    @include space-between;
  }

  .container {
    @include container;
    margin-top: .5rem;
  }

  .menu-wrapper {
    width: 100%;
  }

  // .menu__logo {
  //   width: 42%;
  //   // margin: 0 .8rem;
  //   display: inline-block;
  //   position: absolute;
  //   top: 0;
  //   left: 0;

  //   a {
  //     width: 90%;
  //     height: 2rem;
  //     display: inline-block;
  //      margin: 0 auto;
  //     img {
  //       width: 13rem;
  //       margin: 0 auto;
  //       display: block;
  //     }
  //   }
  // }
</style>
