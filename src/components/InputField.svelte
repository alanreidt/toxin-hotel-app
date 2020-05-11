<script>
  export let labelText = false;
</script>

<style lang="less">
  @import '../styles/variables';
  @import '../styles/mixins';

  .input-field {
    display: inline-block;
    vertical-align: middle;
    width: 100%;
    margin-bottom: 20px;

    color: #colors[dark-shade-75];

    &__label {
      display: inline-block;
      vertical-align: middle;
      width: 100%;
    }

    &__text {
      #box.input-text();
    }
  }

  .input-field__input {
    .body-text();

    padding: 0;

    display: inline-block;
    vertical-align: middle;

    width: 100%;
    height: 2.75rem;
    padding-left: 0.9375rem;

    background-color: #fff;
    outline: none;

    border: 1px solid #colors[dark-shade-25];
    border-radius: 0.25rem;

    box-sizing: border-box;

    transition: border-color 0.25s ease;

    &:hover,
    &:focus {
      border-color: #colors[dark-shade-50];
    }

    &::placeholder {
      // make firefox styles compatible with others
      opacity: 1;

      color: #colors[dark-shade-25];
    }
  }
</style>

<div class="input-field">
  <label class="input-field__label">
    {#if labelText}
      <span class="input-field__text">{labelText}</span>
    {/if}

    <input class="input-field__input" type="text" max-length="24" {...$$restProps}>
  </label>
</div>
