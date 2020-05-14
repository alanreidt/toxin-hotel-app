<script>
  export let title;
  export let description;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .media {
    display: flex;
    flex-flow: row wrap;
    align-items: center;

    &__picture {
      display: block;
      margin-right: 10px;
    }

    &__text {
      .body-text();
    }

    &__title {
      display: block;
      margin-top: 0;
      margin-bottom: 2px;

      font-weight: 700;
    }

    &__description {
      display: block;
      margin-top: 0;
      margin-bottom: 0;
    }
  }
</style>

<div class="media" {...$$restProps}>
  <div class="media__picture">
    <slot></slot>
  </div>
  <div class="media__text">
    <span class="media__title">{title}</span>
    <span class="media__description">{@html description}</span>
  </div>
</div>
