<template>
  <div class="filter-results-wrapper" id="dealers">
    <div class="filter-results" :class="{ addHeight: show }">
      <div class="container">
        <div class="filter-results__filter" v-show="windowWidth < 750">
          <h1 class="dealer-amount">{{ filterDealers.length }} dealers</h1>
          <button @click="show = !show">
            <h1>Filter Results</h1>
            <span>&#9662;</span>
          </button>
        </div>
        <div class="filter-results__filter" v-show="windowWidth >= 750">
          <h1 class="dealer-amount">{{ filterDealers.length }} dealers</h1>
          <h1 class="filter-results__title">Filter Results</h1>
        </div>
        <div class="filter-results__options" :class="{ show: show }">
          <div class="option" v-for="(option, index) in options" :key="index">
            <input type="checkbox"
                  name="service"
                  v-model="checkedOptions"
                  :value="option">
            <span></span>
            <label for="service">{{ (option.split(' '))[0] }}</label>
          </div>
        </div>
      </div>
    </div>
    <Dealers :filterDealers="filterDealers"></Dealers>
  </div>
</template>

<script>
import Dealers from './Dealers.vue'

export default {
  name: 'filterResults',
  components: { Dealers },
  props: ['dealers', 'windowWidth'],
  data () {
    return {
      show: false,
      checkedOptions: [],
      options: ['Service Pro', 'Installation Pro', 'Residential Pro', 'Commercial Pro'],
      proArr: [],
      service: true,
      installation: true,
      residential: true,
      commercial: true
    }
  },
  computed: {
    filterDealers (event) {
      if (!this.checkedOptions.length) return this.dealers

      let proArr = this.dealers.filter((dealer) => {
        for (let i = 0; i < this.checkedOptions.length; i++) {
          if (!dealer.data.certifications.includes(this.checkedOptions[i])) return false
        }
        return true
      })
      return proArr
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .filter-results {
    width: 100%;
    height: 8rem;
    font-family: $text-primary;
    z-index: 0;
    background-color: $off-white;

    @include md {
      height: 7rem;
      border-radius: .6rem;
      margin: 0 auto;
    }

    @include lg {
      width: 99.2rem;
    }
  }

  .addHeight {
    height: 30rem;
  }

  .container {
    @include container;
    width: 100%;
    position: relative;
    @include md {
      // width: 76.8rem;
      width: 100%;
      height: 7rem;
      @include center-vertical;
      @include space-around;
    }
  }

  .filter-results__filter {
    width: 27.3rem;
    height: 6rem;
    margin: 0 auto;
    // z-index: 3;
    @include space-between;

    @include md {
      @include center-vertical;
      height: auto;
      width: auto;
      margin: 0;
    }

    .dealer-amount {
      width: 8rem;
      height: 2rem;
      margin-top: 2.7rem;
      color: $blue;
      font-size: 1.7rem;
      text-align: center;

      @include md {
        width: 10rem;
        height: 4rem;
        margin-top: 0;
        color: $blue;
        font-size: 1.8rem;
        text-align: center;
        border-right: .1rem solid $lighter-gray;
        @include center-vertical;
      }
    }

    .filter-results__title {
      width: 10rem;
      height: 2rem;
      margin-top: .6rem;
      padding-left: 2rem;
      font-size: 1.4rem;
      text-align: center;
    }

     button {
      width: 16.4rem;
      height: 4rem;
      margin-top: 1.8rem;
      display: block;
      border: .1rem solid $lighter-gray;
      font-size: 1.5rem;
      font-family: $text-primary;
      font-weight: 700;
      cursor: pointer;
      background-color: $color-white;

      h1 {
        font-size: 1.5rem;
        width: 12rem;
        margin-top: 1.1rem;
        float: left;
      }

      span {
        float: right;
        display: block;
        width: 4rem;
        height: 3rem;
        border-left: .1rem solid $lighter-gray;
        padding-top: 1rem;
        background-color: $off-white;
        text-align: center;
      }
    }
  }

  // check boxes
  .filter-results__options {
    display: none;
    width: 27.3rem;
    height: 20rem;
    margin: 0 auto;
    background-color: $color-white;

    @include md {
      @include center-vertical;
      display: block;
      position: relative;
      opacity: 1;
      transform: none;
      width: auto;
      height: 7rem;
      margin: 0;
      background-color: $off-white;
    }
  }

  .show {
    display: block;
  }

  .option {
    @include center-vertical;
    position: relative;
    height: 5rem;
    padding-left: 1.5rem;

    @include md {
      display: inline-block;
      height: 4rem;
      width: 13rem;
      padding: 2.3rem 0 0 0;
    }
    span {
      display: block;
      position: relative;
      border-radius: .4rem;
      width: 2.4rem;
      height: 2.4rem;
      background-color: $blue;
      border: .1rem solid $gray;

      @include md {
        display: inline-block;
      }

      &::before {
        content: "";
        position: absolute;
        border-radius: .2rem;
        width: 2.4rem;
        height: 2.4rem;
        top: 0;
        left: 0;
        background-color: #eaecec;

        @include md {
          background-color: white;
        }
      }
    }

    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      width: 90%;
      height: 2.5rem;
      z-index: 1;

      @include md {
        width: 80%;
      }

      &:hover {
        + span::before {
          background-color: $lighter-gray;
        }
      }

      &:checked {
        + span::before {
          width: .8rem;
          height: .8rem;
          top: .8rem;
          left: .8rem;
          border-radius: 0;
          transition: .2s ease-in-out;
          background-color: $color-white;
        }
      }

      &:not(:checked) {
        + span::before {
          width: 2.4rem;
          height: 2.4rem;
          top: 0;
          left: 0;
          border-radius: .2rem;
          transition: .2s ease-in-out;
          background-color: $lighter-gray;

          @include md {
            background-color: $color-white;
          }
        }
      }
    }

    label {
      display: block;
      width: 12rem;
      font-size: 1.2rem;
      padding-left: 1rem;

      @include md {
        position: absolute;
        display: inline-block;
        width: 8rem;
        font-size: 1.2rem;
        margin-top: .6rem;
      }
    }
  }
</style>
