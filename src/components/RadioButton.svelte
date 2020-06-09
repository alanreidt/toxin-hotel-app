<script>
  export let labelText;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @radio-button-width: 20px;
  @radio-button-border-width: 1px;
  @radio-button-padding: 4px;
  @radio-button-inner-elem-diameter: @radio-button-width - 2 *
    @radio-button-padding;

  .radio-button {
    display: inline-block;
    vertical-align: middle;

    margin-right: 20px;
    box-sizing: border-box;

    &:last-child {
      margin-right: 0;
    }

    &__label {
      display: inline-block;
      vertical-align: middle;
      width: 100%;

      cursor: pointer;
    }

    &__input {
      .default-styles-reset();
      margin: 0;

      position: relative;
      z-index: 100;

      display: inline-block;
      vertical-align: middle;
      width: @radio-button-width;
      height: @radio-button-width;
      margin-right: 10px;

      background-color: transparent;
      border: @radio-button-border-width solid #colors[dark-shade-25];
      // border-radius: 50%;
      border-radius: 10px;
      cursor: pointer;

      box-sizing: border-box;

      &:checked {
        // border: 1px solid #colors[primary];
        border-color: #colors[primary];
      }

      &:checked + .radio-button__text {
        color: #colors[dark-shade-75];
      }

      &:checked::before {
        background-image: @primary-gradient;
      }
    }

    &__input::after,
    &__input::before {
      content: "";
      position: absolute;
      z-index: 200;

      // aligns in the center
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);

      width: @radio-button-inner-elem-diameter;
      height: @radio-button-inner-elem-diameter;
      border-radius: 50%;
      background-color: transparent;

      transition: all 0.25s ease-out;
    }

    &__text {
      .not-selectable();
      .body-text();

      display: inline-block;
      vertical-align: middle;

      line-height: @radio-button-width;
      color: #colors[dark-shade-50];
    }
  }
</style>

<div class="radio-button">
  <label class="radio-button__label">
    <input class="radio-button__input" type="radio" {...$$restProps} />
    <span class="radio-button__text">{labelText}</span>
  </label>
</div>
