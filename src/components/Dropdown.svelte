<script>
  import Expander from "./Expander.svelte";
  import InputField from "./InputField.svelte";
  import DropdownMenu from "./DropdownMenu.svelte";

  export let labelText;
  export let options;
  export let hasButtonPane;

  let isExpanded = false;

  $: inputValue = composeString(options) || "Сколько гостей";

  function composeString(options) {
    const guestsQuantity = options[0].value + options[1].value;
    const guestsStr = `${guestsQuantity} ${
      guestsQuantity === 1 ? "гость" : "гостя"
    }`;
    const babiesQuantity = options[2].value;
    const babiesStr = `${babiesQuantity} ${
      babiesQuantity === 1 ? "младенец" : "младенца"
    }`;

    return [guestsStr, babiesStr]
      .filter((item) => Number(item[0]) !== 0)
      .join(", ");
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .dropdown {
    &_is-expanded &__trigger {
      color: #colors[dark-shade-75];
    }

    &__trigger {
      position: relative;
      color: #colors[dark-shade-50];

      &::after {
        .material-icons();
        font-size: 1.5rem;

        content: "\e5cf";
        position: absolute;
        bottom: 0;
        right: 0;

        display: inline-block;
        vertical-align: middle;

        width: 2.75rem;
        height: 2.75rem;
        line-height: 2.75rem;

        text-align: center;
        color: inherit;
        background-color: transparent;

        box-sizing: border-box;
        pointer-events: none;
      }
    }

    &_is-expanded :global(&__input) {
      border-color: #colors[dark-shade-50];
      border-bottom-left-radius: 0;
      border-bottom-right-radius: 0;
    }

    &__menu {
      margin-top: -1 * @dropdown-menu-border-size;
    }
  }
</style>

<div class="dropdown {isExpanded ? 'dropdown_is-expanded' : ''}">
  <Expander bind:isExpanded>
    <div on:focusin|stopPropagation slot="trigger" class="dropdown__trigger">
      <InputField
        class="dropdown__input"
        value={inputValue}
        readonly={true}
        {labelText}
        {...$$restProps} />
    </div>
    <div slot="menu" class="dropdown__menu">
      <DropdownMenu bind:options {hasButtonPane} />
    </div>
  </Expander>
</div>
