<template>
  <div class="navbar" id="navbar">
    <div class="container">
      <div class="nav-sm" v-show="windowWidth < 768">
        <div class="menu__logo">
          <a href="#">
            <img src="static/img/pool-pros-logo.png" alt="Pool Pros" title="POOL PROS">
          </a>
        </div>
        <div class="navbar__btn">
          <a href="#" @click="getProDealers">
            <i class="fas fa-map-marker-alt fa-lg"></i>
            Find a Pro
          </a>
        </div>
        <div class="navbar__menu-icon">
          <img src="/static/img/menu-icon-mobile.png" alt="Menu-Icon" @click="openSideNav">
        </div>
        <div class="navbar-mobile-wrapper" :class="{ open : isOpen }">
          <ul class="nav__menu-items-sm">
            <li class="nav__close" @click="openSideNav">
              <span class="nav__close__close">&#10006;</span>
              <a href="#">Home</a>
            </li>
            <li class="nav__menu-item-sm" v-for="(menuLink, index) in menuLinks" :key="index">
              <a class="nav__menu-item__link" href="#" @click="openNav(index)">
                {{ menuLink.menuTitle }}
              </a>
            </li>
          </ul>
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
              <li class="nav__menu-item" v-for="(menuLink, index) in menuLinks" :key="index">
                <a class="nav__menu-title" href="#">
                  <span>{{ menuLink.menuTitle }}</span>
                </a>
              </li>
            </ul>
          </div>
          <div class="navbar__btn">
            <a href="#" @click="getProDealers">
              <i class="fas fa-map-marker-alt fa-lg"></i>
              Find a Pool Pro
            </a>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import dealers from './dealer.json'

export default {
  name: 'navBar',
  props: ['windowWidth'],
  data () {
    return {
      isOpen: false,
      openSubMenu: false,
      dealers: dealers.dealers,
      menuLinks: [
        { menuTitle: 'Pools & Spas' },
        { menuTitle: 'Supplies' },
        { menuTitle: 'Resources' },
        { menuTitle: 'Services' }
      ]
    }
  },
  methods: {
    openSideNav () {
      this.isOpen = !this.isOpen
      this.$emit('openSideNav', this.isOpen)
    },
    getProDealers (e) {
      this.$emit('getProDealers', this.dealers)
      e.preventDefault()
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
      font-size: 1.15rem;
      font-weight: 900;
      text-align: center;
      cursor: pointer;
      transition: .5s;

      @include center-vertical;

      &:hover {
        border-color: lighten($blue, 20%);
        color: lighten($blue, 20%);
      }

      @include md {
      width: 13rem;
      padding: 0 1rem;
    }
      // img
      svg {
        height: 1.8rem;
        margin: 0 .4rem 0 1rem;
        color: $blue;
        transition: .5s;

        @include md {
          margin: 0 .4rem 0 .5rem;
        }
      }
    }

    a:hover svg {
      color: lighten($blue, 20%);
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
      width: 40rem;
      position: relative;
      margin: 0 auto;
      @include center-vertical
    }
  }

  .nav__menu-item {
    margin-top: 1rem;
    list-style: none;
    @include md {
      width: 10rem;
      height: 4rem;
      margin-top: 3rem;
      list-style: none;
      @include horizontal-list;
      cursor: pointer;
    }

    .nav__menu-title {
      @include md {
        display: block;
        width: 10rem;
        height: 4rem;
        font-size: 1.4rem;
        font-weight: 700;
        color: $blue;
        text-decoration: none;
        text-align: center;
        cursor: pointer;

        span {
          width: max-content;
          margin: 0 auto;
          position: relative;
          display: block;
          &::before {
            @include animateUnderline;
          }
        }
        &:hover span::before {
          @include hoverUnderline;
        }
      }
    }
  }

  // mobile side nav
  .navbar-mobile-wrapper {
    height:100%;
    width:0;
    position:fixed;
    z-index:1;
    top:0;
    right: 0;
    background-color: $color-white;
    overflow-x:hidden;
    padding-top: 2rem;
    transition:0.5s;
  }

  .open {
    width: 25rem;
    overflow-x:hidden;
  }

  .nav__menu-item-sm {
    width: 25rem;
    height: 4rem;
    margin: 0 auto;
    list-style: none;
    display: block;
    @include center-vertical;

    &:hover {
      background-color: $off-white;
    }

    .nav__menu-item__link {
      text-decoration: none;
      font-size: 1.4rem;
      font-weight: 700;
      color: $blue;
      width: 80%;
      height: 4rem;
      display: block;
      margin: 0 auto;
      text-align: center;

      @include center-vertical;
    }
  }

  .nav__close {
    width: 25rem;
    height: 3.3rem;
    padding: 0 2rem;
    font-size: 2rem;
    color: $light-gray;
    list-style: none;
    cursor: pointer;
    border-bottom: .1rem solid $lighter-gray;

  .nav__close__close {
    display: inline-block;
    padding-bottom: .5rem;
  }

    a {
      width: 16rem;
      display: inline-block;
      text-align: center;
      text-decoration: none;
      font-family: $text-secondary;
      font-size: 1.8rem;
      font-weight: 700;
      color: $blue;
    }
  }
</style>
