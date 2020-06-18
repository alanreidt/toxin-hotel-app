<script>
  import Box from "./Box.svelte";
  import InputField from "./InputField.svelte";
  import Button from "./Button.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .entry-box {
    &__row {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__item {
      #box.item();
    }

    &__alternate-entry {
      #box.alternate-entry();
    }

    &__text {
      #box.text();
    }
  }
</style>

<div class="entry-box">
  <Box>
    <h2 slot="title" class="entry-box__title">Войти</h2>
    <form name="entry-box-form" autocomplete="on">
      <div class="entry-box__row">
        <div class="entry-box__item">
          <InputField
            type='email'
            name='email'
            placeholder='Email'
            autocomplete='email'
            spellcheck='false'
            required='true'
          />
        </div>
        <div class="entry-box__item">
          <InputField
            type='password'
            name='password'
            placeholder='Пароль'
            maxlength='20'
            autocomplete='current-password'
            spellcheck='false'
            required='true'
          />
        </div>
      </div>
      <div class="entry-box__row">
        <div class="entry-box__item">
          <Button text="Войти" mods="full-width" />
        </div>
      </div>
    </form>
    <div slot="footer" class="entry-box__footer">
      <div class="entry-box__alternate-entry">
        <p class="entry-box__text">Нет аккаунта на Toxin?</p>
        <Button text="Создать" mods="secondary" href="/mock-address/change-me" />
      </div>
    </div>
  </Box>
</div>
