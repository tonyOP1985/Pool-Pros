<template>
  <div class="navbar">
    <div class="container">
      <div class="nav-sm" v-show="windowWidth < 768">
        <div class="menu__logo">
          <a href="#">
            <img src="static/img/pool-pros-logo.png" alt="Pool Pros" title="POOL PROS">
          </a>
        </div>
        <div class="navbar__btn">
          <a href="#">
            <img src="/static/img/location-icon.png" alt="location" title="Find a Pool Pro">
            Find a Pro
          </a>
        </div>
        <div class="navbar__menu-icon">
          <img src="/static/img/menu-icon-mobile.png" alt="Menu-Icon" v-on:click="openSideNav">
        </div>
        <div class="nav__menu-sm" v-bind:class="{ open : isOpen }">
          <!-- todo: change to v-show to get transition functionality -->
          <!-- <transition name="fade"> -->
            <NavBarMobileDropDown v-bind:menuLinks="menuLinks"></NavBarMobileDropDown>
          <!-- </transition> -->
        </div>
      </div>
      <div class="nav-lg" v-show="windowWidth >= 768">
          <div class="menu__logo">
            <a href="#">
              <img src="static/img/pool-pros-logo.png" alt="Pool Pros" title="POOL PROS">
            </a>
          </div>
          <div class="nav__menu">
            <ul class="nav__menu-items">
              <li class="nav__menu-item" v-for="(menuLink, index) in menuLinks" v-bind:key="index">
                <a href="#">
                  {{ menuLink.menuTitle }}
                </a>
                <ul class="nav__submenu">
                  <li v-for="(item, index) in menuLink.menuItems" v-bind:key="index">
                    <a href="#">{{ item }}</a>
                  </li>
                </ul>
              </li>
            </ul>
          </div>
          <div class="navbar__btn">
            <a href="#">
              <img src="/static/img/location-icon.png" alt="location" title="Find a Pool Pro">
              Find a Pool Pro
            </a>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavBarMobileDropDown from './NavBarMobileDropDown.vue'

export default {
  name: 'navBar',
  components: {
    NavBarMobileDropDown
  },
  props: ['windowWidth'],
  data () {
    return {
      // windowWidth: 0,
      isOpen: false,
      menuLinks: [
        {
          menuTitle: 'Pools & Spas',
          id: 0,
          menuItems: [
            'Above Ground Pools',
            'In Ground Pools',
            'Spas'
          ]
        },
        {
          menuTitle: 'Supplies',
          id: 1,
          menuItems: [
            'Vaccum Heads & Hoses',
            'Chlorine Tabs & Powder',
            'Solar Blankets',
            'Winter/Saftey Covers',
            'Winter Supplies',
            'Pumps & Filters',
            'Heaters & more'
          ]
        },
        {
          menuTitle: 'Resources',
          id: 2,
          menuItems: [
            'Cleaning',
            'Filters',
            'Frodo and Sam\'s Clean Pool Club',
            'Shire Pools'
          ]
        },
        {
          menuTitle: 'Services',
          id: 3,
          menuItems: [
            'Residential Maintenace',
            'Openings & Closings',
            'Pool and Spa Renovations',
            'Vinyl Liner Replacement & Repair',
            'Safety Covers',
            'Automatic Pool & Spa Covers',
            'Landscaping'
          ]
        }
      ]
    }
  },
  methods: {
    openSideNav () {
      this.isOpen = !this.isOpen
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .navbar {
    width: 100%;
    height: 5rem;
    font-family: $text-primary;
    // display: inline-block;

    @include lg {
      height: 8rem;
    }
  }
  .container {
    width: 100%;

    @include xl {
      width: 110rem;
      margin: 0 auto;
    }
  }
  .nav-sm {
    width: 100%;
    height: 5rem;
    @include space-between;
  }
  .nav-lg {
    width: 100%;
    height: 5rem;
    @include space-between;

    @include lg {
      height: 8rem;
      @include center-vertical;
    }
  }

  .menu__logo {
    width: 13rem;
    height: 3rem;
    margin: 1.7rem 0 0 1rem;
    display: inline-block;

    @include lg {
      width: 21rem;
      height: 3rem;
      margin: 0 0 0 2rem;
    }

    a {
      width: 13rem;
      height: 2rem;
      display: inline-block;
      margin: 0 auto;

      @include lg {
        width: 21rem;
        height: 3rem;
      }
      img {
        width: 13rem;
        margin: 0 auto;
        display: block;

        @include lg {
          width: 21rem;
          height: 3rem;
        }
      }
    }
  }
  .navbar__btn {
    width: 10rem;
    display: inline-block;
    margin-top: .9rem;

    @include md {
      width: 15.5rem;
    }

    @include lg {
      margin: 0 2rem 0 0;
    }

    a {
      margin: 0;
      width: 10rem;
      height: 3.2rem;
      background: none;
      border: 1px solid $blue;
      border-radius: .3rem;
      color: $blue;
      text-transform: uppercase;
      text-decoration: none;
      font-weight: 900;
      text-align: center;
      cursor: pointer;

      @include center-vertical;

      @include md {
      width: 13rem;
      padding: 0 1rem;
    }

      img {
        height: 1.8rem;
        margin: 0 .4rem 0 1rem;

        @include md {
          margin: 0 .4rem 0 .5rem;
        }
      }
    }
  }
  .navbar__menu-icon {
    width: 5.5rem;
    display: inline-block;
    position: relative;
    z-index: 1;
    margin: .7rem .3rem 0 0;
    img {
      width: 5.5rem;
      cursor: pointer;
    }
  }
  .nav__menu {
    @include md {
      width: 45rem;
      position: relative;
      margin-top: 0;
      @include center-vertical
    }
    @include lg {
      margin-left: 15%;
    }
  }

  .nav__menu-item {
    @include md {
      width: auto;
      height: auto;
      margin: 1rem 0 0 0;
      @include horizontal-list;
    }

    a {
      @include md {
        width: auto;
        font-size: 1.4rem;
        font-weight: 700;
        color: $blue;
        text-decoration: none;
        background: url(/static/img/down-arrow.png) no-repeat right;
        background-size: .8rem;
        padding: 1.8rem;
      }
    }
  }

 .nav__submenu {
    display: none;
    position: absolute;
    min-width: 22rem;
    padding-top: 2.7rem;
    z-index: 2;

    li {
      list-style: none;

      a {
        color: $dark-blue;
        font-size: 1.2rem;
        background: none;
        background-color: #fff;
        padding: 1.2rem 1.6rem;
        display: block;

        &:hover {
          background-color: #eee;
        }
      }
    }
  }
  .nav__menu-item:hover .nav__submenu {
    display: block;
  }

  .nav__menu-sm {
    width: 100%;
    display: none;
    height: 100vh;
    position: fixed;
    top:0;
    left: 0;
    margin-top: 5rem;
    // background-color: #ebebeb;
    background-color: #fff;
    overflow: hidden;
    transition: .5s;
  }

  .open {
    display: block;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>
