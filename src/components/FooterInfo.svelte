<script>
  import Logo from "./Logo.svelte";
  import Socials from "./Socials.svelte";
  import FooterNav from "./FooterNav.svelte";
  import FooterSubscription from "./FooterSubscription.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .footer-info {
    .block-default-styles();

    border-top: 1px solid rgba(31, 32, 65, 0.1);
    border-bottom: 1px solid rgba(31, 32, 65, 0.1);

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
      align-items: flex-start;
      padding-top: 100px;
      padding-bottom: 100px;

      @media (max-width: @site-width) {
        padding-top: 90px;
        padding-bottom: 90px;
      }

      @media (max-width: 1187px) {
        justify-content: space-evenly;
        padding-top: 75px;
        padding-bottom: 75px;
      }

      @media (max-width: 853px) {
        padding-top: 65px;
        padding-bottom: 65px;
      }

      @media (max-width: 577px) {
        padding-top: 55px;
        padding-bottom: 55px;
      }

      @media (max-width: 517px) {
        padding-top: 45px;
        padding-bottom: 45px;
      }
    }

    &__item {
      flex: 0 0 260px;
      margin-right: 60px;
    }

    &__item_for_logo {
      @media (max-width: 1187px) {
        flex: 0 1 560px;
        order: 3;
        margin: 40px auto 0;
      }

      @media (max-width: 853px) {
        flex: 1 1 260px;
        order: 2;
        max-width: 320px;
        margin: 0;
        margin-right: 5%;
      }

      @media (max-width: 577px) {
        flex: 1 1 100%;
        order: 3;
        max-width: 500px;
        margin-right: 0;
      }
    }

    &__item_for_footer-nav {
      flex: 1 1 auto;
      max-width: 540px;

      @media (max-width: 1187px) {
        margin-right: 7%;
      }

      @media (max-width: 853px) {
        flex-basis: 100%;
        max-width: 100%;
        margin-right: 0;
        margin-bottom: 50px;
      }

      @media (max-width: 577px) {
        margin-bottom: 40px;
      }
    }

    &__item_for_footer-subscription {
      margin-right: 0;

      @media (max-width: 1187px) {
        flex: 1 1 260px;
        max-width: 320px;
      }

      @media (max-width: 853px) {
        order: 3;
      }

      @media (max-width: 577px) {
        order: 2;
        margin-bottom: 40px;
      }
    }

    &__brand-mark {
      @media (max-width: 1187px) {
        text-align: center;
      }

      @media (max-width: 853px) {
        text-align: left;
      }

      @media (max-width: 577px) {
        text-align: center;
      }
    }

    & :global(&__logo) {
      @media (max-width: 1187px) {
        text-align: center;
      }

      @media (max-width: 853px) {
        text-align: left;
      }

      @media (max-width: 577px) {
        text-align: center;
      }
    }

    &__socials {
      display: none;

      @media (max-width: 577px) {
        display: flex;
        justify-content: center;
        margin-top: 20px;

        .socials__item {
          margin-right: 25px;
        }

        .socials__item:last-child {
          margin-right: 0;
        }
      }
    }
  }
</style>

<div class="footer-info">
  <div class="footer-info__container">
    <div class="footer-info__inner">
      <div class="footer-info__item footer-info__item_for_logo">
        <div class="footer-info__brand-mark">
          <Logo class="footer-info__logo"/>
          <p class="logo__description">
            Бронирование номеров в&nbsp;лучшем отеле 2019 года по&nbsp;версии
            ассоциации &laquo;Отельные взгляды&raquo;
          </p>
        </div>
        <div class="footer-info__socials">
          <Socials/>
        </div>
      </div>
      <div class="footer-info__item footer-info__item_for_footer-nav">
        <FooterNav/>
      </div>
      <div
        class="footer-info__item footer-info__item_for_footer-subscription">
        <FooterSubscription/>
      </div>
    </div>
  </div>
</div>
