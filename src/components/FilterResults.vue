<template>
  <div class="filter-results">
    <div class="container">
      <div class="filter-results__filter">
        <h1 class="dealer-amount">{{ dealers }} dealers</h1>
        <button @click="show = !show">
          <h1>Filter Results</h1>
          <span>&#9662;</span>
        </button>
      </div>
      <div class="filter-results__options" v-bind:class="{ show: show }">
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
  name: 'filterResults',
  data () {
    return {
      show: false,
      dealers: 0
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .filter-results {
    width: 100%;
    height: 30rem;
    // height: 8rem;
    font-family: $text-primary;
    z-index: 0;
    background-color: #eaecec;
  }

  .container {
    @include container;
  }

  .filter-results__filter {
    width: 27.3rem;
    height: 6rem;
    margin: 0 auto;
    @include space-between;

    .dealer-amount {
      width: 8rem;
      height: 2rem;
      margin-top: 2.7rem;
      color: $blue;
      font-size: 1.8rem;
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
        // background-color: $off-white;
        background-color: #eaecec;
        text-align: center;
      }
    }
  }

  // check boxes
  .filter-results__options {
    // display: block;
    display: none;
    width: 27.3rem;
    height: 20rem;
    // height: 0;
    margin: 0 auto;
    background-color: $color-white;
  }

  .show {
    display: block;
    // height: 20rem;
  }

  .option {
    @include center-vertical;
    position: relative;
    height: 5rem;
    padding-left: 1.5rem;
    span {
      display: block;
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
        background-color: #eaecec;
      }
    }

    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      width: 90%;
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
          background-color: $lighter-gray;
        }
      }
    }

    label {
      display: block;
      width: 12rem;
      font-size: 1.2rem;
      padding-left: 1rem;
    }
  }
</style>
