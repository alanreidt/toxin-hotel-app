<script>
  export let items;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .bullet-list {
    margin-top: 0;
    margin-bottom: 0;
    padding-left: 20px;

    list-style: disc outside url("./bullet-list-bullet.svg");

    &__item {
      .body-text();

      margin-bottom: 10px;

      &:last-child {
        margin-bottom: 0;
      }
    }
  }
</style>

<ul class="bullet-list" {...$$restProps}>
  {#each items as item}
    <li class="bullet-list__item">{@html item}</li>
  {/each}
</ul>
