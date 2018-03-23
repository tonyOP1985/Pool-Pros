<template>
  <div class="jumbotron">
    <div class="jumbotron-overlay">
      <div class="jumbotron__message-main">
        <h1>Is your pool ready for Summer?</h1>
      </div>
      <div class="jumbotron__message-tag">
        <p>A pool pro is ready to help!</p>
      </div>
      <div class="jumbotron__message-hr">
        <hr>
      </div>
      <div class="jumbotron__message-sub">
        <p>Choose a pro that's close to your home from the list below.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'jumbotron'
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .jumbotron {
    width: 100%;
    height: 40rem;
    background-image: url(/static/img/Hero-image-mobile.png);
    background-size: cover;
    background-position: center;
    background-repeat: none;
    position: relative;
    overflow: hidden;
    z-index: -1;

    @include sm {
      height: 35rem;
    }
    @include md {
      background-image: url(/static/img/hero-image-desktop.png);
      height: 35rem;
    }
    @include xl {
      height: 35rem;
    }
    @include custom(1400) {
      height: 45rem;
    }
  }

  @mixin inner-overlay {
    width: 75%;
    position: absolute;
  }

  .jumbotron-overlay {
    width: 100%;
    height: 100%;
    font-family: $text-secondary;
    letter-spacing: .1rem;
    position: relative;
    @include sm {
      height: 35rem;
    }
    @include md {
      height: 35rem;
    }
    @include xl {
      height: 35rem;
    }
    @include custom(1400) {
      height: 45rem;
    }

    .jumbotron__message-main {
      @include inner-overlay;
      top: 19%;
      left: 12%;

      @include sm {
        top: 26%;
      }
      @include lg {
        top: 23%;
      }
        h1 {
        color: #fff;
        font-size: 2.5rem;
        font-weight: 300;
        font-family: $text-secondary;
        text-align: center;
        text-shadow: 1px 1px 8px rgba(0, 0, 0, 0.5);

        @include sm {
          font-size: 3rem;
        }
        @include md {
          font-size: 3rem;
        }
        @include lg {
          font-size: 5rem;
        }
      }
    }

    .jumbotron__message-tag {
      @include inner-overlay;
      top: 44%;
      left: 12%;
      @include lg {
        top: 45%;
      }
      p {
        text-transform: uppercase;
        font-size: 1.3rem;
        font-weight: 700;
        color: rgb(91, 184, 214);
        text-align: center;
        text-shadow: 1px 1px 8px rgba(0, 0, 0, 0.8);
        @include lg {
          font-size: 2rem;
        }
      }
    }

    .jumbotron__message-sub {
      @include inner-overlay;
      top: 70%;
      left: 12%;
      p {
        font-size: 1.3rem;
        font-weight: 400;
        color: #fff;
        text-align: center;
        letter-spacing: 0;
        font-family: $text-secondary;

        @include lg {
          // font-size: 1.5rem;
          font-size: 1.8rem;
        }
      }
    }

    .jumbotron__message-hr {
      @include inner-overlay;
      top: 58%;
      left: 12%;

      @include lg {
        top: 60%;
      }
    }

    hr {
      width: 13rem;
      margin: 0 auto;
    }
  }
</style>
