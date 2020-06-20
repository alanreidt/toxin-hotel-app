<script>
  import Socials from "./Socials.svelte";

  const currentYear = new Date().getFullYear();
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .bottomline {
    .block-default-styles();

    height: var(--topline-height);

    @media (max-width: 577px) {
      height: auto;
    }

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row nowrap;
      justify-content: space-between;
      align-items: center;

      @media (max-width: 577px) {
        justify-content: center;
        text-align: center;

        padding-top: 15px;
        padding-bottom: 15px;
      }
    }

    &__copyright {
      .body-text();

      margin-top: 0;
      margin-bottom: 0;
      line-height: 1.5;

      @media (max-width: 640px) {
        font-size: 13px;
      }
    }

    &__socials {
      @media (max-width: 577px) {
        display: none;
      }
    }
  }
</style>

<div class="bottomline">
  <div class="bottomline__container">
    <div class="bottomline__inner">
      <p class="bottomline__copyright">
        Copyright &copy;&nbsp;{currentYear} Toxin отель. Все права защищены.
      </p>
      <div class="bottomline__socials">
        <Socials />
      </div>
    </div>
  </div>
</div>
