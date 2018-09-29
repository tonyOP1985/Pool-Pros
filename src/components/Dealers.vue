<template>
  <div class="dealers-wrapper">
    <div class="dealers" v-if="!filterDealers"></div>
    <div class="dealers" else>
      <div
        class="dealer-info"
        v-for="(dealer, index) in filterDealers"
        :key="index">

        <h1>{{ dealer.data.name }}</h1>
        <hr>
        <div class="phone-wrapper">
          <button
            class="dealer-info__phone">
            <img src="/static/img/phone-icon-mobile.png" alt="phone">
            <span class="tap">
              Tap to call
            </span>
            <span class="phone">
              {{ removeDash(dealer.data.phone1) }}
            </span>
          </button>

          <div class="dealer-info__phone__md">
            <img src="/static/img/phone-icon-desktop.png" alt="phone">
            <span class="phone">
              {{ removeDash(dealer.data.phone1) }}
            </span>
          </div>
        </div>

        <p>Can't talk? Click below to send an email.</p>
        <button
          class="dealer-info__email">
          <img src="/static/img/email-icon.png" alt="email">
          <span class="contact">Contact this Pro</span>
        </button>

        <div class="dealer-info__hours">
          <h1>Business Hours</h1>
          <ul>
            <li>Weekdays {{ proClosed(dealer.data.weekHours.mon) }}</li>
            <li>Saturdays {{ proClosed(dealer.data.weekHours.sat) }}</li>
            <li>Sundays {{ proClosed(dealer.data.weekHours.sun) }}</li>
          </ul>
        </div>

        <div class="dealer-info__certifactions">
          <ul class="dealer-info__wrapper">
            <li v-for="(certification, index) in dealer.data.certifications" :key="index">
              <img :src="addCertImage(certification)" :alt="certification">
              {{ certification }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dealers',
  props: ['filterDealers'],
  data () {
    return {
      dealers: [],
      certImage: [
        { name: 'Installation', image: 'star-installation-pro.png' },
        { name: 'Commercial', image: 'users-commercial-pro.png' },
        { name: 'Residential', image: 'home-residential-pro.png' },
        { name: 'Service', image: 'gear-service-pro.png' }
      ],
      operationOpen: []
    }
  },
  methods: {
    // replaces dashes in phone numbers with periods
    removeDash (str) {
      let newStr = str.replace(/-/g, '.');
      return newStr;
    },
    // gets appropriate image for each certification
    addCertImage (cert) {
      //  remove "pro" from certification name before selecting correct image
      let newStr = (cert.replace(/pro/i, '')).trim();
      let imageUrl = this.certImage.find(i => newStr === i.name).image;
      return `/static/img/${imageUrl}`;
    },
    proClosed (hours) {
      if (hours === '') {
        return '- Closed';
      } else if (hours === 'On Call') {
        return '- On Call';
      } else {
        return hours;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .dealers-wrapper {
    @include md {
      max-width: 100%;
      margin-top: 5rem;
    }
    @include lg {
      width: 99.2rem;
      margin: 5rem auto 0 auto;
    }
  }

  .dealers {
    width: 100%;
    background-color: $color-white;

    @include md {
      display: flex;
      flex-wrap: wrap;
    }
  }

  .dealer-info {
    width: 30rem;
    margin: 2rem auto;
    padding-top: 2rem;
    border: .1rem solid $lighter-gray;
    border-radius: .4rem;

    @include md {
      border-radius: .6rem;
      margin: 2rem auto;
      display: inline-block;
      box-shadow: 0 3px 10px -1px $light-gray;
    }

    @include lg {
      margin: 2rem 0 2rem 2.4rem;
    }

    h1 {
      width: 100%;
      font-family: $text-secondary;
      font-size: 1.6rem;
      font-weight: 300;
      text-align: center;
      margin: 0 auto;
      padding: 2rem 0;
    }

    p {
      width: 100%;
      text-align: center;
      font-family: $text-secondary;
      font-size: .9rem;
      font-style: italic;
      padding: 2rem 0;
    }

    hr {
      display: none;

      @include md {
        display: block;
        height: .1rem;
        width: 90%;
        border: 0;
        border-top: 1px solid $off-white;
        margin: 0 auto 2rem auto;
        padding: 0;
      }
    }

    .phone-wrapper {
      @include md {
        width: 100%;
        height: 4rem;
      }
    }

    .dealer-info__phone {
      position: relative;
      display: block;
      width: 21rem;
      height: 3.1rem;
      border: none;
      border-radius: .3rem;
      background-color: $light-blue;
      color: $color-white;
      margin: 0 auto;
      cursor: pointer;

      @include md {
        display: none;
      }

      img {
        display: inline-block;
        position: absolute;
        left: .4rem;
        top: .4rem;
        height: 2.3rem;
        margin: 0;
      }

      .tap {
        display: inline-block;
        position: absolute;
        left: 3.5rem;
        top: 1.2rem;
        font-size: .8rem;
        letter-spacing: .1rem;
      }

      .phone {
        display: inline-block;
        position: absolute;
        left: 8.8rem;
        top: .8rem;
        font-size: 1.4rem;
        font-weight: 600;
        letter-spacing: .1rem;
      }
    }

    .dealer-info__phone__md {
      display: none;
      @include md {
        position: relative;
        display: block;
        width: 21rem;
        height: 3.1rem;
        border: none;
        margin: 0 auto;
      }

      img {
        display: inline-block;
        position: absolute;
        left: 1.5rem;
        top: .7rem;
        height: 2.5rem;
        margin: 0;
      }

      .phone {
        display: inline-block;
        position: absolute;
        left: 5rem;
        top: .8rem;
        font-family: $text-secondary;
        font-size: 1.8rem;
        font-weight: 600;
        letter-spacing: .1rem;
      }
    }

    .dealer-info__email {
      position: relative;
      display: block;
      width: 17rem;
      height: 3.5rem;
      border: .1rem solid $light-gray;
      border-radius: .3rem;
      background-color: $color-white;
      margin: 0 auto;
      cursor: pointer;

      img {
        display:inline-block;
        position: absolute;
        top: 1.2rem;
        left: 1.8rem;
        height: 1.2rem;
      }

      .contact {
        display: inline-block;
        position: absolute;
        top: .8rem;
        left: 2.3rem;
        width: 15rem;
        font-family: $text-primary;
        font-size: 1.4rem;
        color: $dark-blue;
        font-weight: 600;
      }
    }

    .dealer-info__hours {
      h1 {
        font-size: 1.2rem;
        font-weight: 600;
        padding-bottom: 0;
      }

      ul {
        width: 100%;
        font-family: $text-primary;
        li {
          width: 50%;
          margin: .5rem auto 0  auto;
          list-style: none;
          text-align: center;
        }
      }
    }

    .dealer-info__certifactions {
      width: 100%;
      height: 7rem;
      // background-color: $off-white;
      background-color: #eaecec;
      margin-top: 2rem;
      font-family: $text-primary;

      .dealer-info__wrapper {
        width: 80%;
        height: 4rem;
        margin: 0 auto;
        padding-top: 2rem;

          li {
          display: inline-block;
          position: relative;
          width: 10rem;
          height: 2rem;
          padding-left: 2rem;
          img {
            display: inline-block;
            height: 1rem;
          }
        }
      }
    }
  }
</style>
