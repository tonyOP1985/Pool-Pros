<template>
  <div class="navbar-mobile-wrapper" :class="{ open : isOpen }">
    <ul class="nav__menu-items-sm">
      <li class="nav__close">&#10006;</li>
      <li class="nav__menu-item-sm" v-for="(menuLink, index) in menuLinks" :key="index">
        <a class="nav__menu-item__link" href="#" @click="openNav(index)">
          {{ menuLink.menuTitle }}
        </a>
        <ul class="nav__submenu-sm" v-show="show[index].subOpen">
          <li class="nav__close" @click="openNav(index)">&#10006;</li>
          <li v-for="item in menuLink.menuItems" :key="item">
            <a class="nav__subitem" href="#">{{ item }}</a>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'NavBarMobile',
  props: ['menuLinks', 'isOpen'],
  data () {
    return {
      // isOpen: false,
      show: [{subOpen: false}, {subOpen: false}, {subOpen: false}, {subOpen: false}],
      close: true
    }
  },
  methods: {
    // openSubNav () {
    //   this.isOpen = !this.isOpen
    // },
    openNav (n) {
      this.show[n].subOpen = !this.show[n].subOpen
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .navbar-mobile-wrapper {
    height:100%;
    width:0;
    position:fixed;
    z-index:1;
    top:0;
    left:0;
    background-color: $color-white;
    overflow-x:hidden;
    padding-top: 2rem;
    transition:0.5s;
  }

  .open {
    width: 25rem;
  }

  .close {
    width: 0;
  }

  .nav__menu-item-sm {
    width: 25rem;
    height: 3rem;
    margin: 0 auto;
    list-style: none;
    display: block;
    @include center-vertical;

    .nav__menu-item__link {
      text-decoration: none;
      font-size: 1.4rem;
      font-weight: 700;
      color: $blue;
      background: url(/static/img/next-arrow.png) no-repeat right;
      background-size: .8rem;
      width: 12rem;
      width: 80%;
      display: block;
      margin: 0 auto;
      text-align: center;

      &:hover {
        color: lighten($blue, 15%);
      }
    }
  }

  .nav__submenu-sm {
    list-style: none;
    text-decoration: none;
    // display: none;
    width: 100%;
    height: 50vh;
    // background-color: #ebebeb;
    background-color: #fff;
    position: absolute;
    top: -5rem;
    margin-top: 5rem;
    z-index: 1;

    li {
      height: 3rem;
    }
  }

  .nav__subitem {
    text-decoration: none;
    font-size: 1.4rem;
    font-weight: 700;
    color: $blue;
    background-size: .8rem;
    // width: 12rem;
    width: 80%;
    display: block;
    margin: 0 auto;
    text-align: center;

    &:hover {
      color: lighten($blue, 15%);
    }
  }

  .open {
    display: block;
  }

  .nav__close {
    padding: 0 2rem;
    font-size: 2rem;
    float: right;
    color: $light-gray;
    list-style: none;
    cursor: pointer;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>
