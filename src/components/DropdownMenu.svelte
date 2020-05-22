<script>
  import Counter from "./Counter.svelte";
  import Button from "./Button.svelte";

  export let options;
  export let hasButtonPane = false;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .dropdown-menu {
    .h3-text();

    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0.9375rem;
    padding-right: 0.4375rem;

    background-color: #fff;
    border: @dropdown-menu-border-size solid #colors[dark-shade-50];
    border-bottom-left-radius: 0.25rem;
    border-bottom-right-radius: 0.25rem;

    box-sizing: border-box;

    // transition: height 0.3s ease-out;

    &__option {
      display: flex;
      flex-direction: row;
      justify-content: space-between;

      margin-bottom: 1.375rem;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__option-text {
      display: inline-block;
      vertical-align: middle;
    }

    &__button-pane {
      display: flex;
      flex-direction: row;
      justify-content: space-between;

      padding-top: 0.4375rem;
    }
  }
</style>

<div class="dropdown-menu">
  {#each options as {name, value, min, max}}
    <div class="dropdown-menu__option">
      <span class="dropdown-menu__option-text">{name}</span>
      <div class="dropdown-menu__counter">
        <Counter bind:value {min} {max} />
      </div>
    </div>
  {/each}

  {#if hasButtonPane}
    <div class="dropdown-menu__button-pane">
      <Button text="Очистить" mods="reset" />
      <Button text="Применить" />
    </div>
  {/if}
</div>
