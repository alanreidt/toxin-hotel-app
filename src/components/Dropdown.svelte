<script>
  import InputField from "./InputField.svelte";
  import DropdownMenu from "./DropdownMenu.svelte";

  export let labelText;
  export let options;
  export let hasButtonPane;

  let isExpanded = false;
  $: inputValue = composeString(options) || 'Сколько гостей';

  function composeString(options) {
    const guestsQuantity = options[0].value + options[1].value;
    const guestsStr = `${guestsQuantity} ${guestsQuantity === 1 ? 'гость' : 'гостя'}`;
    const babiesQuantity = options[2].value;
    const babiesStr = `${babiesQuantity} ${babiesQuantity === 1 ? 'младенец' : 'младенца'}`;

    return [guestsStr, babiesStr].filter((item) => Number(item[0]) !== 0).join(", ");
  }

  function toggleIsExpanded() {
    isExpanded = !isExpanded;
  }

  const SPACE_KEY = " ";

  function handleTriggerKeydown(event) {
    if (event.key === "Enter" || event.key === SPACE_KEY) {
      event.preventDefault();

      toggleIsExpanded();
    }

    if (event.key === "Escape" || event.key === "Esc") {
      event.preventDefault();

      isExpanded = false;
    }
  }

  function handleTriggerClick() {
    toggleIsExpanded();
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .dropdown {
    position: relative;
    z-index: 200;

    display: inline-block;
    vertical-align: middle;
    width: 100%;

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
        top: 0;
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

    &_is-expanded &__menu {
      pointer-events: auto;
      opacity: 1;
    }

    &__menu {
      position: absolute;
      z-index: 200;
      width: 100%;
      top: 100%;
      left: 0;

      opacity: 0;
      pointer-events: none;
    }
  }
</style>

<div class="dropdown js-dropdown {isExpanded ? 'dropdown_is-expanded' : ''}">
  <div
    class="dropdown__trigger js-dropdown__trigger"
    on:keydown={handleTriggerKeydown}
    on:click={handleTriggerClick}>
    <InputField
      value={inputValue}
      readonly={true}
      {labelText}
      {...$$restProps} />
  </div>
  <div class="dropdown__menu js-dropdown__menu">
    <DropdownMenu bind:options {hasButtonPane} />
  </div>
</div>
