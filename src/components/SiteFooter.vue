<template>
  <footer>
    <div class="footer__top">
      <div class="container">
        <div class="footer__top__media">
          <div class="logo">
            <img src="/static/img/pool-pros-logo-footer.png" alt="Pool Pros" title="Pool Pros">
          </div>
          <div class="social-media">
            <h1>Connect with us</h1>
            <div class="social-icons">
              <a href="#">
                <img class="social-icons__facebook" src="/static/img/facebook-icon.png" alt="Facebook" title="Facebook">
              </a>
              <a href="#">
                <img class="social-icons__twitter" src="/static/img/twitter-icon.png" alt="Twitter" title="Twitter">
              </a>
              <a href="#">
                <img class="social-icons__youtube" src="/static/img/youtube-icon.png" alt="YouTube" title="YouTube">
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer__bottom">
      <div class="container">
        <div class="footer__bottom__commercial">
          <ul>
            <li><a href="#">Dealers and Distributors</a></li>
            <li>
              <a href="#">
                Commercial Service
                <img src="/static/img/action-commercial-icon.png" alt="Commerical Login" title="Commerical Login">
              </a>
            </li>
          </ul>
        </div>
        <div class="footer__bottom__links">
          <ul>
            <li><a href="#">&copy; 2017 Pool Pros</a></li>
            <li><a href="#">Privacy Policy</a></li>
            <li><a href="#">Terms and Conditions</a></li>
          </ul>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'siteFooter'
}
</script>

<style lang="scss" scoped>
  @import "../assets/app.scss";

  footer {
    display: block;
    z-index: 1;
  }

  .footer__top {
    height: 14rem;
    width: 100%;
    background-color: $dark-blue;
  }

  .container {
    @include container;
    @include space-around;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }

  .logo {
    width: 18.8rem;
    margin: 4rem auto 3rem auto;
    img {
      height: 2.6rem;
    }
  }

  .footer__top__media {
    width: 100%;
    height: 100%;
    position: relative;
  }
  .social-media {
    height: 3rem;
    width: 80%;
    margin: 0 auto;
    @include space-between;
    @include custom(396) {
      width: 30.3rem;
    }
    h1 {
      color: $off-white;
      font-family: $text-primary;
      font-size: 1.4rem;
      text-transform: uppercase;
      padding-top: .2rem;
    }

    img {
      display: inline-block;
    }
  }

  .social-icons {
    width: 10rem;
    @include space-between;
  }

  .social-icons__facebook {
    height: 2rem;
    width: 1rem;
  }

  .social-icons__twitter {
    height: 2rem;
    width: 2rem;
  }

  .social-icons__youtube {
    height: 2rem;
    width: 2rem;
  }

  // footer bottom

  .footer__bottom {
    height: 8rem;
    width: 100%;
    background-color: $light-blue;
    color: $off-white;
    font-family: $text-primary;
    font-size: .9rem;
  }

  .footer__bottom__commercial {
    height: 4rem;
    width: 30rem;
    margin: 0 auto;
    position: relative;
    @include space-around;
    @include center-vertical;
    &::before {
      content: "";
      position: absolute;
      height: .1rem;
      width: 90%;
      bottom: 0;
      left: 1.3rem;
      border-bottom: .1rem solid $off-white;
    }
    @include custom(380) {
        width: 30rem;
        margin: 0 auto;
    }

    ul {
      display: block;
      height: 2rem;
      width: 25rem;
      li {
        height: 2rem;
        list-style: none;
        display: inline-block;
        &:nth-child(2)::before {
        content: "|";
        padding: 0 1.2rem 0 1rem;
        }
        a{
          display: inline-block;
          height: 2rem;
          text-decoration: none;
          color: $off-white;
          padding-top: .5rem;
          position: relative;

          &:hover {
            text-decoration: underline;
          }
          img {
            display: inline-block;
            height: 1.1rem;
            width: 1.1rem;
            position: absolute;
            top: .5rem;
            left: 10rem;
          }
        }
      }
    }
    @include md {
      display: none;
    }
  }

  .footer__bottom__links {
    height: 4rem;
    width: 100%;
    @include center-vertical;

    ul {
      width: auto;
      margin: 0 auto;
      display: flex;
      flex-direction: row;
      height: 2rem;

      li {
        list-style: none;
        width: 8rem;
        &:first-child::after {
          content: "";
          padding-left: 1.8%;
        }
        &:nth-child(2)::before {
          content: "|";
          padding: 0 .7rem;
        }
        &:nth-child(3)::before {
          content: "|";
          padding: 0 .7rem;
        }
        &:last-child {
          width: 11.5rem;
        }

        a {
          text-decoration: none;
          color: $off-white;

          &:hover {
            text-decoration: underline;
          }
        }
      }
    }
  }
</style>
