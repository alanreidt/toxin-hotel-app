<script>
  import PaginationDisplay from "./PaginationDisplay.svelte";

  export let itemsPerPage = 12;
  export let itemsInTotal = 100;
  export let currentPage = 1;

  const roundNumberBy = function(number, boundary) {
    if (number < boundary) {
      return number;
    }

    const result = Math.floor(number / boundary) * boundary;

    return `${result}+`;
  }

  const roundedTotal = roundNumberBy(itemsInTotal, 100);

  const findIndex = function(currentPage, itemsPerPage, start = 0) {
    return start + (currentPage - 1) * itemsPerPage;
  }

  $: currentIndex = findIndex(currentPage, itemsPerPage + 1);
  $: firstItemIndex = Math.max(1, currentIndex);
  $: lastItemIndex = currentIndex + itemsPerPage;

  $: text = `${firstItemIndex}—${lastItemIndex} из ${roundedTotal} вариантов аренды`;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .pagination {
    &__text {
      .body-text();
      .not-selectable();

      margin-top: 10px;
      margin-bottom: 0;

      text-align: center;
    }
  }
</style>

<div class="pagination">
  <PaginationDisplay bind:currentPage {itemsPerPage} {itemsInTotal} />
  <p class="pagination__text">{text}</p>
</div>
