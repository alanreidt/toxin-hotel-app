<script>
  import Media from "./Media.svelte";

  export let title;
  export let description;
  export let materialIconName;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .cell-block {
    padding-top: 20px;
    padding-bottom: 20px;

    border-top: 1px solid #colors[dark-shade-10];

    &:first-child {
      padding-top: 0;
      border-top: 0;
    }

    &__icon {
      font-size: 48px;
      color: #colors[primary];
    }
  }
</style>

<div class="cell-block" {...$$restProps}>
  <Media {title} {description}>
    <i class="material-icons cell-block__icon">{materialIconName}</i>
  </Media>
</div>
