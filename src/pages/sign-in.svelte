<script>
  import EntryBox from "../components/EntryBox.svelte";

  import { metatags } from '@sveltech/routify';

  metatags.title = "Вход в аккаунт";
  metatags.description = "change-me";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .sign-in {
    .block-default-styles();
    background: url(/images/registration-bg.jpg) #333 bottom/cover no-repeat;

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row wrap;
      justify-content: center;

      padding-top: 160px;
      padding-bottom: 160px;
    }

    &__entry-box {
      .block-default-styles();
      max-width: 380px;
    }
  }
</style>

<!-- routify:options name="sign-in" index=false -->

<div class="sign-in">
  <div class="sign-in__container">
      <div class="sign-in__inner">
          <div class="sign-in__entry-box">
            <EntryBox />
          </div>
      </div>
  </div>
</div>
