<script>
  import DateInputField from "./DateInputField.svelte";
  import InputField from "./InputField.svelte";
  import StatefulInput from "./StatefulInput.svelte";
  import Button from "./Button.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .registration-box {
    #box();

    &__inner {
      #box.inner();
    }

    &__row {
      #box.row();
    }

    &__title {
      #box.title();
    }

    &__input-text {
      #box.input-text();
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

<div class="registration-box">
  <div class="registration-box__inner">
    <div class="registration-box__row">
      <h2 class="registration-box__title">Регистрация аккаунта</h2>
    </div>
    <form name="registration-box-form" autocomplete="on">
      <div class="registration-box__row">
        <div class="registration-box__item">
          <InputField
            name='fname'
            placeholder='Имя'
            maxlength='25'
            autocomplete='given-name'
            spellcheck='true'
            required='true'
          />
        </div>
        <div class="registration-box__item">
          <InputField
            name='lname'
            placeholder='Фамилия'
            maxlength='25'
            autocomplete='family-name'
            spellcheck='true'
            required='true'
          />
        </div>
        <div class="registration-box__item">
          <StatefulInput
            labelText='Мужчина'
            type='radio'
            name='registration-box-sex'
            value='man'
            checked
          />
          <StatefulInput
            labelText='Женщина'
            type='radio'
            name='registration-box-sex'
            value='woman'
          />
        </div>
      </div>
      <div class="registration-box__row">
        <div class="registration-box__item">
          <DateInputField
            labelText= 'Дата рождения'
            name='bday'
            maxlength='10'
            autocomplete='bday'
            required
          />
        </div>
      </div>
      <div class="registration-box__row">
        <div class="registration-box__item">
          <span class="registration-box__input-text">
            Данные для входа в сервис
          </span>
          <InputField
            type='email'
            name='email'
            placeholder='Email'
            autocomplete='email'
            spellcheck='false'
            required='true'
          />
        </div>
        <div class="registration-box__item">
          <InputField
            type='password'
            name='password'
            placeholder='Пароль'
            maxlength='20'
            autocomplete='new-password'
            spellcheck='false'
            required='true'
          />
        </div>
        <div class="registration-box__item">
          <StatefulInput
            labelText='Получать спецпредложения'
            mods='type_toggle'
            id='registration-box-mailing'
            type='checkbox'
            name='registration-box-mailing'
            value='on'
          />
        </div>
      </div>
      <div class="registration-box__row">
        <div class="registration-box__item">
          <Button text="перейти к оплате" mods="full-width" />
        </div>
      </div>
      <div class="registration-box__row">
        <div class="registration-box__item">
          <div class="registration-box__alternate-entry">
            <p class="registration-box__text">Уже есть аккаунт на Toxin?</p>
            <Button text="Войти" mods="secondary" href="/mock-address/change-me" />
          </div>
        </div>
      </div>
    </form>
  </div>
</div>
