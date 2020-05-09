<script>
  export let labelText;
</script>

<style lang="scss">
  @import '../styles/variables';

  .input-field {
    display: inline-block;
    vertical-align: middle;
    width: 100%;

    &__label {
      display: inline-block;
      vertical-align: middle;
      width: 100%;
    }
  }

  .input-field__input {
    padding: 0;
    display: inline-block;
    vertical-align: middle;
    width: 100%;
    height: 2.75rem;
    padding-left: 0.9375rem;
    background-color: #fff;
    outline: none;
    border-radius: 0.25rem;
    box-sizing: border-box;
    transition: border-color 0.25s ease;
  }

  .input-field__input::placeholder {
    opacity: 1;
  }
</style>

<div class="input-field">
  <label class="input-field__label">
    {labelText}
    <input class="input-field__input">
  </label>
</div>
