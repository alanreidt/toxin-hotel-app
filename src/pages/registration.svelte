<script>
  import RegistrationBox from "../components/RegistrationBox.svelte";

  import { metatags } from '@sveltech/routify';

  metatags.title = "Регистрация аккаунта";
  metatags.description = "change-me";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .registration {
    .block-default-styles();
    background: url(/images/registration-bg.jpg) #333 bottom/cover no-repeat;

    &__container {
      .container();

      @media (max-width: 365px) {
        padding-right: 10px;
        padding-left: 10px;
      }
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row wrap;
      justify-content: center;

      padding-top: 30px;
      padding-bottom: 26px;

      @media (max-width: 380px + 2 * @site-paddings[small]) {
        padding-top: 20px;
        padding-bottom: 20px;
      }

      @media (max-width: 365px) {
        padding-top: 15px;
        padding-bottom: 15px;
      }
    }

    &__registration-box {
      .block-default-styles();
      max-width: 380px;
    }
  }
</style>

<!-- routify:options name="registration" index=false -->

<div class="registration">
  <div class="registration__container">
      <div class="registration__inner">
          <div class="registration__registration-box">
            <RegistrationBox />
          </div>
      </div>
  </div>
</div>
