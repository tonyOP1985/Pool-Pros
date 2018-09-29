<template>
  <div class="directions">
    <div class="container">
      <div class="direction__steps">
        <div class="steps">
          <div class="steps__img">
            <img src="/static/img/1-circle.png" alt="Step 1">
          </div>
          <div class="steps__info">
            <h1>Choose a pro</h1>
            <p>Click "Find a Pro" at the top, then choose a pro from the list below.</p>
          </div>
        </div>
        <div class="steps">
          <div class="steps__img">
            <img src="/static/img/2-circle.png" alt="Step 2">
          </div>
          <div class="steps__info">
            <h1>Contact a pro</h1>
            <p>Email a pro to make an appointment for pool & spa services or installation.</p>
          </div>
        </div>
        <div class="steps visit">
          <div class="steps__img">
            <img src="/static/img/3-circle.png" alt="Step 3">
          </div>
          <div class="steps__info">
            <h1>A pro visits</h1>
            <p class="visit-p">A pro will visit your home and assess your pool & spa needs.</p>
          </div>
        </div>
      </div>
    </div>
    <div class="water-img"></div>
  </div>
</template>

<script>
export default {
  name: 'directions'
};
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .directions {
    font-family: $text-secondary;
  }

  .steps__img {
    img {
      display: block;
      width: 5rem;

      @include md {
        width: 6rem;
      }
    }
  }

  .direction__steps {
    max-width: 100%;

    @include md {
      @include space-around;
    }
    @include lg {
      width: 99.2rem;
      margin: 0 auto;
    }
  }

  .container {
    @include container;
    @include lg {
      width: 100%;
    }
  }

  .steps {
    @include space-around;

    width: 26.6rem;
    margin: 2rem auto;

    @include md {
      margin: 2rem 0;
      overflow: hidden;
    }
  }

  .steps__info {
    padding: 0 0 0 1rem;
    width: 20.2rem;
    h1 {
      font-size: 1.5rem;
      font-weight: 700;
      color: $dark-blue;
      text-transform: uppercase;
    }
    p {
      color: $light-gray;
      font-size: 1.1rem;
      line-height: 1.5rem;
      padding-top: .4rem;
    }

    @include md {
      padding-top: 1rem;
    }
  }

  .visit {
    width: 26.6rem;

    @include md {
      width: 23rem;
    }
  }

  .visit-p {
    width: 16rem;
  }

  .water-img {
    width: 100%;
    height: 15rem;
    background-image: url(/static/img/water-image.png);
    background-size: cover;
    background-position: top;
    @include xl {
      height: 20rem;
    }
  }
</style>
