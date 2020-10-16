<script>
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .footer-subscription {
    .block-default-styles();

    text-align: left;

    @media (max-width: 577px) {
      text-align: center;
    }

    &__inner {
      .block-default-styles();
    }

    &__title {
      .h3-text();

      margin-top: 0;
      margin-bottom: 20px;
    }

    &__description {
      .body-text();

      margin-top: 0;
      margin-bottom: 20px;
    }
  }
</style>

<aside class="footer-subscription">
  <div class="footer-subscription__inner">
    <h3 class="footer-subscription__title">Подписка</h3>
    <p class="footer-subscription__description">
      Получайте специальные предложения и&nbsp;новости сервиса
    </p>
  </div>
</aside>
