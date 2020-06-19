<script>
  import Button from "./Button.svelte";

  export let userName = false;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @button-border-width: 2px;
  @username-height: 30px;

  .entrance {
    @media (max-width: 1050px) {
      padding-left: 15px;
      padding-right: 15px;
    }

    &__button-group {
      display: flex;
      flex-flow: row nowrap;

      @media (max-width: 1050px) {
        flex-flow: column nowrap;
        align-items: center;
      }
    }

    &__button-wrapper {
      margin-right: 20px;

      &:last-child {
        margin-right: 0;
      }

      @media (max-width: 1050px) {
        margin-right: 0;
        margin-bottom: 10px;

        &:last-child {
          margin-bottom: 0;
        }
      }
    }

    & :global(&__button) {
      @button-height: 34px;

      height: @button-height;
      line-height: @button-height - 2 * @button-border-width;

      &_main {
        line-height: @button-height;
      }
    }

    &__username-wrapper {
      display: block;
      width: 100%;
      box-sizing: border-box;

      @media (max-width: 1050px) {
        text-align: center;
      }
    }

    &__username {
      .not-selectable();
      .body-text();
      margin-top: 0;
      margin-bottom: 0;

      display: inline-block;
      vertical-align: middle;
      height: @username-height;
      line-height: @username-height;
      padding-left: 30px;

      color: #colors[dark-shade-50];
      border-left: 1px solid rgba(31, 32, 65, 0.1);
      text-transform: capitalize;

      box-sizing: border-box;

      @media (max-width: 1050px) {
        height: auto;
        padding-left: 0;
        padding-top: 10px;

        line-height: inherit;
        border-left: 0;
        border-top: 1px solid rgba(31, 32, 65, 0.1);
      }
    }
  }
</style>

<div class="entrance">
  {#if userName}
    <div class="entrance__username-wrapper">
      <span class="entrance__username">{userName}</span>
    </div>
  {:else}
    <div class="entrance__button-group">
      <div class="entrance__button-wrapper">
        <Button
          class="button entrance__button"
          text="Войти"
          mods="secondary"
          href="/mock-address/change-me" />
      </div>
      <div class="entrance__button-wrapper">
        <Button
          class="button entrance__button entrance__button_main"
          text="Зарегистрироваться"
          mods="main"
          href="/mock-address/change-me" />
      </div>
    </div>
  {/if}
</div>
