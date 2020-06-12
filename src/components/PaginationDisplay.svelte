<script>
  export let itemsPerPage = 12;
  export let itemsInTotal = 100;
  export let currentPage = 1;
  export let maxPageQuantity = 5;
  export let pagesToDisplay = 3;

  const pagesInTotal = Math.ceil(itemsInTotal / itemsPerPage);
  const pageNumbers = new Array(pagesInTotal).fill(1).map((value, index) => index + 1);

  const isMaxPageQuantityExceeded = pagesInTotal > maxPageQuantity;
  const currentPageIndex = currentPage - 1;

  $: displayedPageNumbers = isMaxPageQuantityExceeded ?
    pageNumbers.slice(currentPageIndex, currentPageIndex + pagesToDisplay) :
    pageNumbers;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .pagination-display {
    display: block;
    width: 100%;

    &__list {
      .list-styles-reset();

      display: flex;
      flex-flow: row nowrap;
      justify-content: center;
    }

    &__link {
      .body-text();
      text-decoration: none;

      display: inline-block;
      vertical-align: middle;
      width: 40px;
      height: 40px;
      line-height: 40px;

      font-size: 12px;
      text-align: center;
      background-image: transparent;
      color: #colors[dark-shade-50];
      border-radius: 50%;

      &:hover,
      &:focus {
        background-color: #colors[dark-shade-25];
      }
    }

    &__link_active {
      background-image: @primary-gradient;
      color: #fff;

      &:hover,
      &:focus {
        opacity: 0.5;
      }
    }

    &__link_arrow {
      // .arrow();
      .decoration_type_arrow-forward();
      &::before {
        // styles for .decoration_type_arrow-forward();
        width: inherit;
        height: inherit;
        line-height: inherit;
        color: #fff;
      }

      background-image: @secondary-gradient;

      &:hover,
      &:focus {
        opacity: 0.5;
      }
    }
  }
</style>

<div class="pagination-display">
  <ul class="pagination-display__list">
    {#each displayedPageNumbers as pageNumber}
      <li class="pagination-display__item">
        <a
          class="pagination-display__link {pageNumber === currentPage ? "pagination-display__link_active" : ''}"
          href="mock-address/change-me">
          {pageNumber}
        </a>
      </li>
    {/each}

    {#if (isMaxPageQuantityExceeded)}
      <li class="pagination-display__item">
        <a class="pagination-display__link">...</a>
      </li>
      <li class="pagination-display__item">
        <a
          class="pagination-display__link"
          href="mock-address/change-me">
          {pageNumbers[pageNumbers.length - 1]}
        </a>
      </li>
    {/if}

    <li class="pagination-display__item">
      <a
        class="pagination-display__link pagination-display__link_arrow"
        href="/mock-address/change-me"></a>
    </li>
  </ul>
</div>
