<script>
  import InputField from "./InputField.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .subscription-field {
    position: relative;

    &__button {
      .not-selectable();

      position: absolute;
      bottom: 0;
      right: 0;

      // reset <button>, <input> styles
      padding: 0;
      border: none;
      background-color: transparent;

      // reset <a> styles
      text-decoration: none;

      // add compatibility between html elements (<a>, <button>, <input>)
      cursor: pointer;

      // add standart behavior of a <button> to compatibility with <a>
      // isolate component's rules from external influence
      display: inline-block;
      vertical-align: middle;

      width: 44px;
      height: 44px;
      line-height: 44px;

      // add standart behavior of a <button> to compatibility with <a>
      // isolate component's rules from external influence
      box-sizing: border-box;

      color: #colors[primary];
      text-align: center;
      text-overflow: ellipsis;
      overflow: hidden;

      &::before {
        .material-icons();

        content: "\e5c8";
        font-size: 24px;

        display: inline-block;
        vertical-align: middle;

        color: inherit;
      }
    }
  }
</style>

<div class="subscription-field">
  <form
    class="subscription-field__form"
    name="subscription-field-form"
    autocomplete="on">
    <InputField
      type='email'
      name='email'
      placeholder='Email'
      maxlength='24'
      autocomplete='email'
      spellcheck='false'
      {...$$restProps}
    />
    <button class="subscription-field__button" />
  </form>
</div>
