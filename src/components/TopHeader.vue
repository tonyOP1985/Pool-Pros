<template>
  <div class="top-header">
    <div class="container">
      <div class="top-header__links">
        <a class="top-header__links__dist" href="#">Dealers and Distributors</a>
        <a class="top-header__links_service" href="#">
          Commercial Service
          <img src="/static/img/action-commercial-icon.png" alt="Commercial Login" title="Commercial Login">
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'topHeader'
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";
  .top-header {
    display: none;

    @include md {
      display: block;
      width: 100%;
      height: 3.5rem;
      background-color: $dark-blue;
    }
  }

  .container {
    width: 100%;
    height: 3.5rem;
    display: flex;
    justify-content: flex-end;
    @include center-vertical;

    @include xl {
      width: 109rem;
      margin: 0 auto;
    }
  }

  .top-header__links {
    height: 3.5rem;
    text-align: right;
    margin-right: 2rem;
    @include center-vertical;
  }

  .top-header__links__dist {
    width: 15rem;
    margin-right: 5rem;
    font-family: $text-primary;
    font-size: 1.2rem;
    text-decoration: none;
    color: $color-white;
  }

  .top-header__links_service {
    width: 15rem;
    font-family: $text-primary;
    font-size: 1.2rem;
    text-decoration: none;
    color: $color-white;
  }

  img {
    height: 1.5rem;
    margin-left: 2rem;
  }
</style>
