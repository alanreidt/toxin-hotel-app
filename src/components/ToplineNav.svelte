<script>
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .topline-nav {
    @link-horizontal-padding: 10px;

    &__semantic-title {
      .visually-hidden();
    }

    &__list {
      .list-styles-reset();

      display: flex;
      flex-flow: row wrap;

      @media (max-width: 1050px) {
        flex-flow: column nowrap;
        // align-items: center;
      }
    }

    &__item {
      .body-text();

      @media (max-width: 1050px) {
        width: 100%;
        box-sizing: border-box;
      }
    }

    &__link {
      .not-selectable();
      text-decoration: none;

      display: inline-block;
      vertical-align: middle;
      padding: 10px @link-horizontal-padding;

      line-height: 18px; /* 17px = 14px * 1.21429 */
      color: #colors[dark-shade-50];

      box-sizing: border-box;

      @media (max-width: 1050px) {
        width: 100%;
        padding: 15px 0;

        text-align: center;
      }

      &:hover,
      &:focus {
        text-decoration: underline;
      }

      &_active {
        font-weight: 700;
        color: #colors[dark-shade-75];
      }
    }

    &__link-icon {
      font-size: 24px;
      line-height: 18px;
      vertical-align: top;
    }
  }
</style>

<nav class="topline-nav">
  <h2 class="topline-nav__semantic-title">main navigation</h2>
  <ul class="topline-nav__list">
    <li class="topline-nav__item">
      <a
        class="topline-nav__link topline-nav__link_active"
        href="../../../src/markup/pages/index.pug">
        Главная
      </a>
    </li>
    <li class="topline-nav__item">
      <a class="topline-nav__link" href="change-me">О нас</a>
    </li>
    <li class="topline-nav__item topline-nav__item_expandable">
      <a class="topline-nav__link" href="change-me">
        Услуги
        <i class="material-icons topline-nav__link-icon" aria-hidden="true">
          expand_more
        </i>
      </a>
    </li>
    <li class="topline-nav__item">
      <a class="topline-nav__link" href="change-me">Вакансии</a>
    </li>
    <li class="topline-nav__item">
      <a class="topline-nav__link" href="change-me">Новости</a>
    </li>
    <li class="topline-nav__item topline-nav__item_expandable">
      <a class="topline-nav__link" href="change-me">
        Соглашения
        <i class="material-icons topline-nav__link-icon" aria-hidden="true">
          expand_more
        </i>
      </a>
    </li>
  </ul>
</nav>
