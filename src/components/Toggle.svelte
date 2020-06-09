<script>
  export let labelText;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @toggle-height: 20px;
  @toggle-width: 2 * @toggle-height;
  @toggle-border-width: 1px;
  @toggle-padding: 4px;
  @toggle-inner-elem-diameter: @toggle-height - 2 *
    @toggle-padding;

  .toggle {
    display: inline-block;
    vertical-align: middle;
    width: 100%;

    /* margin-right: 0; */
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
      width: @toggle-width;
      height: @toggle-height;
      margin-right: 10px;

      background-color: transparent;
      border: @toggle-border-width solid #colors[dark-shade-25];
      // border-radius: 50%;
      border-radius: 10px;
      cursor: pointer;

      box-sizing: border-box;

      &:checked {
        // border: 1px solid #colors[primary];
        border-color: #colors[primary];
      }

      &:checked + .toggle__text {
        color: #colors[dark-shade-75];
      }

      &:checked::before {
        // express through left for work of transition
        left: @toggle-width - @toggle-inner-elem-diameter -
          2 * @toggle-border-width - @toggle-padding;

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

      width: @toggle-inner-elem-diameter;
      height: @toggle-inner-elem-diameter;
      border-radius: 50%;
      background-color: transparent;

      transition: all 0.25s ease-out;
    }

    &__input::before {
      left: @toggle-padding;
      transform: translateY(-50%);

      background-color: #colors[dark-shade-25];
    }

    &__text {
      .not-selectable();
      .body-text();

      display: inline-block;
      vertical-align: middle;

      line-height: @toggle-height;
      color: #colors[dark-shade-50];
    }
  }
</style>

<div class="toggle">
  <label class="toggle__label">
    <input class="toggle__input" type="checkbox" value="on" {...$$restProps} />
    <span class="toggle__text">{labelText}</span>
  </label>
</div>
