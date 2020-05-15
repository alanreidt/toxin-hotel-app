<script>
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .footer-nav {
    .block-default-styles();
    .not-selectable();

    text-align: left;

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;

      @media (max-width: 853px) {
        justify-content: space-around;
      }

      @media (max-width: 517px) {
        justify-content: space-evenly;
      }
    }

    &__section {
      margin-right: 45px;

      &_for_navigation {
        @media (max-width: 380px) {
          width: 100%;
          margin-right: 0;
          text-align: center;
        }
      }

      &_for_about-us {
        @media (max-width: 517px) {
          margin-right: 0;
        }

        @media (max-width: 380px) {
          width: 100%;
          margin-top: 30px;
          text-align: center;
        }
      }

      &_for_support {
        margin-right: 0;

        @media (max-width: 517px) {
          margin-top: 30px;
          width: 100%;
          text-align: center;
        }
      }
    }

    &__semantic-title {
      .visually-hidden();
    }

    &__title {
      .h3-text();

      margin-top: 0;
      margin-bottom: 10px;
    }

    &__list {
      .list-styles-reset();
    }

    &__link {
      .body-text();
      text-decoration: none;

      display: inline-block;
      vertical-align: middle;
      padding-top: 5px;
      padding-bottom: 5px;
      margin: 5px 0;

      line-height: 1.21429; /* 17px = 14px * 1.21429 */
      color: #colors[dark-shade-50];

      &:hover,
      &:focus {
        text-decoration: underline;
      }
    }
  }
</style>

<nav class="footer-nav">
  <div class="footer-nav__inner">
    <h2 class="footer-nav__semantic-title">footer navigation</h2>
    <section
      class="section footer-nav__section footer-nav__section_for_navigation">
      <h3 class="section__title footer-nav__title">Навигация</h3>
      <ul class="list footer-nav__list">
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">О&nbsp;нас</a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Новости</a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">
            Служба поддержки
          </a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Услуги</a>
        </li>
      </ul>
    </section>
    <section
      class="section footer-nav__section footer-nav__section_for_about-us">
      <h3 class="section__title footer-nav__title">О&nbsp;нас</h3>
      <ul class="list footer-nav__list">
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">
            О&nbsp;сервисе
          </a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">
            Наша команда
          </a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Вакансии</a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Инвесторы</a>
        </li>
      </ul>
    </section>
    <section
      class="section footer-nav__section footer-nav__section_for_support">
      <h3 class="section__title footer-nav__title">Служба поддержки</h3>
      <ul class="list footer-nav__list">
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Соглашения</a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">Сообщества</a>
        </li>
        <li class="list__item footer-nav__item">
          <a class="list__link footer-nav__link" href="change-me">
            Связь с&nbsp;нами
          </a>
        </li>
      </ul>
    </section>
  </div>
</nav>
