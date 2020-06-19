<script>
  export let currentPageHref = '';
  export let optionsList = [
    { text: "О нас", href: "/mock-address/change-me", },
    { text: "Услуги", href: "/mock-address/change-me", hasSubMenu: true, },
    { text: "Вакансии", href: "/mock-address/change-me", },
    { text: "Новости", href: "/mock-address/change-me", },
    { text: "Соглашения", href: "/mock-address/change-me", hasSubMenu: true, },
  ];
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
    {#each optionsList as {text, href, hasSubMenu}}
      <li class="topline-nav__item">
        <a
          class="topline-nav__link {href === currentPageHref ? "topline-nav__link_active" : ''}"
          {href}>
          {text}

          {#if hasSubMenu}
            <i class="material-icons topline-nav__link-icon" aria-hidden="true">
              expand_more
            </i>
          {/if}
        </a>
      </li>
    {/each}
  </ul>
</nav>
