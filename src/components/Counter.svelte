<script>
  import { placeNumberBetween } from "../../modules/utilities";

  export let value = 0;
  export let min = 0;
  export let max = 5;
  export let reset = false;

  value = placeNumberBetween(value, min, max);

  $: isValueMin = value === min;
  $: isValueMax = value === max;
  $: if (reset) {
    value = 0;

    reset = false;
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .counter {
    position: relative;
    z-index: 100;

    width: 100%;
    min-width: 5.75rem;

    text-align: center;
    user-select: none;

    &__button {
      padding: 0;
      border: none;
      background-color: transparent;

      position: absolute;
      z-index: 200;
      top: 50%;
      transform: translateY(-50%);

      display: inline-block;
      vertical-align: middle;

      width: 1.875rem;
      height: 1.875rem;

      text-align: center;
      color: #colors[dark-shade-50];
      border: 1px solid #colors[dark-shade-50];
      border-radius: 50%;

      box-sizing: border-box;
      cursor: pointer;

      &_type_subtraction {
        left: 0;
      }

      &_type_addition {
        right: 0;
      }

      &_is-disabled {
        color: #colors[dark-shade-5];
        border-color: #colors[dark-shade-5];
        cursor: initial;
      }
    }

    &__button-icon {
      display: inline-block;
      vertical-align: middle;

      font-size: 1.125rem;

      pointer-events: none;
      box-sizing: border-box;
    }

    &__quantity-display {
      display: inline-block;
      vertical-align: middle;

      padding: 0 10px;
    }
  }
</style>

<div class="counter js-counter">
  <button
    type="button"
    class="counter__button counter__button_type_subtraction {isValueMin ? 'counter__button_is-disabled' : ''}"
    disabled={isValueMin}
    on:click={() => value -= 1}>
    <i class="material-icons counter__button-icon">remove</i>
  </button>
  <span class="counter__quantity-display js-counter__quantity-display">
    {value}
  </span>
  <button
    type="button"
    class="counter__button counter__button_type_addition {isValueMax ? 'counter__button_is-disabled' : ''}"
    disabled={isValueMax}
    on:click={() => value += 1}>
    <i class="material-icons counter__button-icon">add</i>
  </button>
</div>
