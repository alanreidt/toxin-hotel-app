<script>
  import Logo from "./Logo.svelte";
  import ToplineReception from "./ToplineReception.svelte";
  import ToplineHamburger from "./ToplineHamburger.svelte";
  import MenuOverlay from "./MenuOverlay.svelte";

  import scrollLock from 'scroll-lock';

  export let mainPageHref = "/";
  export let currentPageHref;
  export let userName;
  export let optionsList;

  let isToplineHamburgerActive = false;
  let menuOverlay;

  $: if (isToplineHamburgerActive) {
    scrollLock.disablePageScroll(menuOverlay);
  } else {
    scrollLock.enablePageScroll(menuOverlay);
  }

  $: isMainPage = currentPageHref === mainPageHref;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  /** TO DO:
  *   + Rule out problem with vertical align of the button (maybe font family will help)
  *   + Rule out problem with vertical align of the nav__link (maybe that's true)
  *   -
  */

  :root {
    --topline-height: 70px;
    --menu-button-height: 14px;
    --menu-button-padding: 5px;

    @media (max-width: 1050px) {
      --topline-height: 60px;
    }

    @media (max-width: 640px) {
      --topline-height: 50px;
    }
  }

  .topline {
    .block-default-styles();

    position: relative;
    z-index: 700;
    height: var(--topline-height);

    background-color: #fff;
    box-shadow: 0 10px 20px rgba(31, 32, 65, 0.05);

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row nowrap;
      justify-content: space-between;
      align-items: center;
    }

    &__semantic-title {
      .visually-hidden();
    }

    &__logo {
      .logo__img {
        height: 40px;

        @media (max-width: 670px) {
          height: 35px;
        }
      }
    }

    &__link {
      display: block;
      width: 100%;

      text-decoration: none;
    }
  }
</style>

<header class="topline">
  <div class="topline__container">
    <div class="topline__inner">
      <h1 class="topline__semantic-title">toxin</h1>
      <div class="topline__logo">
        {#if isMainPage}
          <Logo />
        {:else}
          <a href={mainPageHref} class="topline__link">
            <Logo />
          </a>
        {/if}
      </div>
      <ToplineReception active={isToplineHamburgerActive} {currentPageHref} {userName} {optionsList} />
      <ToplineHamburger bind:active={isToplineHamburgerActive} />
      <MenuOverlay {menuOverlay} bind:active={isToplineHamburgerActive} />
    </div>
  </div>
</header>
