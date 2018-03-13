<template>
  <div class="filter-results">
    <div class="container">
      <div class="filter-results__filter">
        <h1 class="dealer-amount">{{ dealerLen }} dealers</h1>
        <h1 class="filter-results__title">Filter Results</h1>
      </div>
      <div class="filter-results__options">
        <div class="option">
          <input type="checkbox" name="service" id="service">
          <span></span>
          <label for="service">Service</label>
        </div>
        <div class="option">
          <input type="checkbox" name="installation" id="installation">
          <span></span>
          <label for="installation">Installation</label>
        </div>
        <div class="option">
          <input type="checkbox" name="residential" id="residential">
          <span></span>
          <label for="residential">Residential</label>
        </div>
        <div class="option">
          <input type="checkbox" name="commercial" id="commerical">
          <span></span>
          <label for="Commercial">Commercial</label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'filterResultsLarge',
  props: ['dealers'],
  data () {
    return {
      dealerLen: 0
    }
  },
  mounted () {
    this.dealerLen = this.dealers.length
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";
  .filter-results {
    width: 100%;
    height: 7rem;
    font-family: $text-primary;
    background-color: #eaecec;
    border-radius: .6rem;
    margin: 0 auto;

    @include lg {
      width: 99.2rem;
    }
  }

  .container {
    @include container;
    width: 76.8rem;
    height: 7rem;
    @include center-vertical;
    @include space-around;
  }

  .filter-results__filter {
    @include center-vertical;

    .dealer-amount {
      width: 10rem;
      height: 4rem;
      color: $blue;
      font-size: 1.8rem;
      text-align: center;
      border-right: .1rem solid $lighter-gray;
      @include center-vertical;
    }

    .filter-results__title {
      width: 10rem;
      height: 2rem;
      margin-top: .6rem;
      padding-left: 2rem;
      font-size: 1.4rem;
      text-align: center;
    }
  }

  .filter-results__options {
    @include center-vertical;
    display: block;
    // width: 27.3rem;
    height: 7rem;
  }

  .show {
    display: block;
    // height: 20rem;
  }

  .option {
    @include center-vertical;
    position: relative;
    display: inline-block;
    height: 4rem;
    width: 13rem;
    padding-top: 2.3rem;
    span {
      display: inline-block;
      position: relative;
      border: .05rem solid $lighter-gray;
      border-radius: .4rem;
      width: 2.4rem;
      height: 2.4rem;
      background-color: $blue;

      &::before {
        content: "";
        position: absolute;
        border-radius: .2rem;
        width: 2.4rem;
        height: 2.4rem;
        top: 0;
        left: 0;
        background-color: white;
      }
    }

    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      width: 80%;
      height: 2.5rem;
      z-index: 1;

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
          background-color: $color-white;
        }
      }
    }

    label {
      position: absolute;
      display: inline-block;
      width: 8rem;
      font-size: 1.2rem;
      padding-left: 1rem;
      margin-top: .6rem;
    }
  }
</style>
