<script>
  import PaginationDisplay from "./PaginationDisplay.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .pagination {
    &__text {
      .body-text();

      margin-top: 10px;
      margin-bottom: 0;

      text-align: center;
    }
  }
</style>

<div class="pagination">
  <PaginationDisplay/>
  <p class="pagination__text">1–12 из 100+ вариантов аренды</p>
</div>
