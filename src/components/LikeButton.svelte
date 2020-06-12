<script>
  export let labelText;
  export let dataValue;

  const initialValue = Number(dataValue);
  const checkedValue = initialValue + 1;

  function handleLikeButtonInputClick(event) {
    dataValue = event.target.checked ? checkedValue : initialValue;
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @like-button-width: 20px;
  @like-button-border-width: 1px;
  @like-button-padding: 4px;
  @like-button-inner-elem-diameter: @like-button-width - 2 *
    @like-button-padding;
  @like-button-toggle-width: 2 * @like-button-width;

  .like-button {
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
      width: @like-button-width;
      height: @like-button-width;
      margin-right: 10px;

      background-color: transparent;
      border: @like-button-border-width solid #colors[dark-shade-25];
      // border-radius: 50%;
      border-radius: 10px;
      cursor: pointer;

      box-sizing: border-box;

      &:checked {
        // border: 1px solid #colors[primary];
        border-color: #colors[primary];
      }

      &:checked + .like-button__text {
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

      width: @like-button-inner-elem-diameter;
      height: @like-button-inner-elem-diameter;
      border-radius: 50%;
      background-color: transparent;

      transition: all 0.25s ease-out;
    }

    &__text {
      .not-selectable();
      .body-text();

      display: inline-block;
      vertical-align: middle;

      line-height: @like-button-width;
      color: #colors[dark-shade-50];
    }
  }

  .like-button_type_like-button {
    margin-right: 0;

    & .like-button__input {
      width: @like-button-toggle-width;
      margin-right: 0;

      color: #colors[dark-shade-25];

      &::after,
      &::before {
        color: inherit;

        transform: translateY(-50%);
        transition: all 0.15s ease;
      }

      &::before {
        .material-icons();

        content: "\e87e";

        left: @like-button-padding;
        font-size: 12px;
        border-radius: 0;
      }

      &::after {
        .body-text();

        content: attr(data-value);
        right: 10px;
        width: auto;
        height: auto;

        font-size: 10px;
        color: inherit;
      }

      &:checked {
        color: #colors[primary];
      }

      &:checked::before {
        content: "\e87d";

        background-image: none;
      }
    }

    & .like-button__text {
      .visually-hidden();
    }
  }
</style>

<div class="like-button like-button_type_like-button">
  <label class="like-button__label">
    <input on:click={handleLikeButtonInputClick} class="like-button__input" type="checkbox" data-value={dataValue} value="on" {...$$restProps} />
    <span class="like-button__text">{labelText}</span>
  </label>
</div>
