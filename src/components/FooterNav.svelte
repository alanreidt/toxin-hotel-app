<script>
  export let sections = [
    {
      title: "Навигация",
      optionsList: [
        { text: "О&nbsp;нас", href: "/mock-address/change-me", },
        { text: "Новости", href: "/mock-address/change-me", },
        { text: "Служба поддержки", href: "/mock-address/change-me", },
        { text: "Услуги", href: "/mock-address/change-me", },
      ],
    },
    {
      title: "О&nbsp;нас",
      optionsList: [
        { text: "О&nbsp;сервисе", href: "/mock-address/change-me", },
        { text: "Наша команда", href: "/mock-address/change-me", },
        { text: "Вакансии", href: "/mock-address/change-me", },
        { text: "Инвесторы", href: "/mock-address/change-me", },
      ],
    },
    {
      title: "Служба поддержки",
      optionsList: [
        { text: "Соглашения", href: "/mock-address/change-me", },
        { text: "Сообщества", href: "/mock-address/change-me", },
        { text: "Связь с&nbsp;нами", href: "/mock-address/change-me", },
      ],
    },
  ];
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

      &:first-child {
        @media (max-width: 380px) {
          width: 100%;
          margin-right: 0;
          text-align: center;
        }
      }

      &:nth-child(2) {
        @media (max-width: 517px) {
          margin-right: 0;
        }

        @media (max-width: 380px) {
          width: 100%;
          margin-top: 30px;
          text-align: center;
        }
      }

      &:last-child {
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
  <h2 class="footer-nav__semantic-title">footer navigation</h2>
  <div class="footer-nav__inner">
    {#each sections as {title, optionsList}, index}
      <section
        class="section footer-nav__section">
        <h3 class="section__title footer-nav__title">{@html title}</h3>
        <ul class="list footer-nav__list">
          {#each optionsList as {text, href}}
            <li class="list__item footer-nav__item">
              <a class="list__link footer-nav__link" {href}>{@html text}</a>
            </li>
          {/each}
        </ul>
      </section>
    {/each}
  </div>
</nav>
