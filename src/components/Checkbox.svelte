<script>
  export let labelText;
  export let labelExplanation;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @checkbox-width: 20px;
  @checkbox-border-width: 1px;

  .checkbox {
    display: inline-block;
    vertical-align: middle;
    width: 100%;
    margin-bottom: 11px;

    &:last-of-type {
      margin-bottom: 0;
    }

    &__label {
      display: inline-block;
      vertical-align: middle;
      width: 100%;

      cursor: pointer;
    }

    &__input {
      .default-styles-reset();
      .material-icons();
      font-size: 14px;
      margin: 0;

      float: left;

      // if float isn't active the rules'd be useful
      display: inline-block;
      vertical-align: middle;

      width: @checkbox-width;
      height: @checkbox-width;
      margin-right: 10px;

      // centralizing ::before element
      text-align: center;
      line-height: @checkbox-width - 2 * @checkbox-border-width;

      background-color: transparent;
      border: @checkbox-border-width solid #colors[dark-shade-25];
      border-radius: 4px;

      cursor: pointer;
      box-sizing: border-box;

      &::before {
        content: "\e5ca";
        color: transparent;
      }

      &:checked {
        border-color: #colors[primary];
      }

      &:checked::before {
        color: #colors[primary];
      }
    }

    &__text {
      .body-text();

      // this lets the element to not overlap a floated element,
      // but to become narrower
      display: block;
      overflow: auto;

      line-height: 1.29;
      color: #colors[dark-shade-50];

      // removes the ability to select text
      -webkit-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none;
    }

    &__text-title {
      display: block;
      margin-top: 0;
      margin-bottom: 5px;

      font-weight: 700;
      color: #colors[dark-shade-75];
    }

    &__text-explanation {
      display: block;
      margin-top: 0;
      margin-bottom: 0;

      font-size: 12px;
      line-height: 1.17;
    }
  }
</style>

<div class="checkbox">
  <label class="checkbox__label">
    <input class="checkbox__input" type="checkbox" {...$$restProps} />
    <div class="checkbox__text">
      {#if labelExplanation}
        <span class="checkbox__text-title">{@html labelText}</span>
        <span class="checkbox__text-explanation">{@html labelExplanation}</span>
      {:else}
        {@html labelText}
      {/if}
    </div>
  </label>
</div>
