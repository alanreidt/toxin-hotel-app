<script>
  import Media from "./Media.svelte";
  import StatefulInput from "./StatefulInput.svelte";

  export let authorName;
  export let date;
  export let imgSrc;
  export let liked;
  export let commentText;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .comment {
    display: block;
    width: 100%;
    margin-bottom: 20px;

    box-sizing: border-box;

    &:last-child {
      margin-bottom: 0;
    }

    &__head {
      margin-bottom: 12px;
    }

    &__avatar {
      display: inline-block;
      vertical-align: middle;

      border: 2px solid #fff;
      border-radius: 50%;
      box-shadow: 0 10px 20px rgba(31, 32, 65, 0.1);

      box-sizing: border-box;
    }

    &__body {
      display: flex;
      flex-direction: row wrap;
    }

    &__button {
      margin-right: 15px;
    }

    &__text {
      .body-text();

      margin-top: 0;
      margin-bottom: 0;
    }
  }
</style>

<!-- form, name -->
<div class="comment">
  <div class="comment__head">
    <Media title={authorName} description={date}>
      <img class="comment__avatar" src={imgSrc} alt="commentator's avatar" width="48" />
    </Media>
  </div>
  <div class="comment__body">
    <div class="comment__button">
      <StatefulInput
        labelText='like button'
        mods='type_like-button'
        type='checkbox'
        name='like-button-1'
        value='on'
        checked={liked}
      />
    </div>
    <div class="comment__content">
      <p class="comment__text">{@html commentText}</p>
    </div>
  </div>
</div>
