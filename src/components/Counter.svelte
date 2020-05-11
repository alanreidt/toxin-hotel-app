<script>

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
    class="counter__button counter__button_type_subtraction
    js-counter__subtraction-button">
    <i class="material-icons counter__button-icon">remove</i>
  </button>
  <span class="counter__quantity-display js-counter__quantity-display">0</span>
  <button
    class="counter__button counter__button_type_addition
    js-counter__addition-button">
    <i class="material-icons counter__button-icon">add</i>
  </button>
</div>
