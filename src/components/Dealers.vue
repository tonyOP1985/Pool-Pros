<template>
  <div class="dealers">
    <div
      class="dealer-info"
      v-for="(dealer, index) in dealerList"
      v-bind:key="index">

      <h1>{{ dealer.data.name }}</h1>
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

      <p>Can't talk? Click below to send and email.</p>
      <button
        class="dealer-info__email">
        <img src="/static/img/email-icon.png" alt="email">
        <span class="contact">Contact this Pro</span>
      </button>

      <div class="dealer-info__hours"></div>

      <div class="dealer-info__certifactions">
        <span v-for="(certification, index) in dealer.data.certifications" v-bind:key="index">
          <img :src="addCertImage(certification)" :alt="certification">
          {{ certification }}
        </span>
      </div>

    </div>
  </div>
</template>

<script>
import dealers from './dealer.json'
export default {
  name: 'Dealers',
  data () {
    return {
      dealerList: dealers.dealers,
      certImage: [
        { name: 'Installation', image: 'star-installation-pro.png' },
        { name: 'Commercial', image: 'users-commercial-pro.png' },
        { name: 'Residential', image: 'home-residential-pro.png' },
        { name: 'Service', image: 'gear-service-pro.png' }
      ],
      certImgURL: ''
    }
  },
  methods: {
    removeDash (str) {
      let newStr = str.replace(/-/g, '.')
      return newStr
    },
    addCertImage (cert) {
      let newStr = (cert.replace(/pro/i, '')).trim()
      for (let i = 0; i < this.certImage.length; i++) {
        if (this.certImage[i].name === newStr) {
          return `/static/img/${this.certImage[i].image}`
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  .dealers {
    width: 100%;
    background-color: $color-white;
  }

  .dealer-info {
    width: 30rem;
    margin: 0 auto;
    padding-top: 2rem;
    border: .1rem solid $off-white;

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
        top: 1rem;
        left: 2.3rem;
        width: 15rem;
        font-family: $text-primary;
        font-size: 1.4rem;
        color: $dark-blue;
        font-weight: 600;
      }
    }

    .dealer-info__certifactions {
      width: 100%;
      height: 7rem;
      background-color: $off-white;
      margin-top: 2rem;
      font-family: $text-primary;

      span {
        img {
          height: 1rem;
        }
      }
    }
  }
</style>
