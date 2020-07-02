<script>
  import Pagination from "./Pagination.svelte";
  import RoomBox from "./RoomBox.svelte";

  const items = new Array(15).fill(1);

  const room888Options = {
    href: "/mock-address/change-me",
    imageSources: ["images/room-888.jpg", "images/room-840.jpg"],
    number: 888,
    price: 9990,
    isLuxe: true,
    rating: 5,
    reviewsQuantity: 145,
  };

  const room840Options = {
    href: "/mock-address/change-me",
    imageSources: ["images/room-840.jpg", "images/room-888.jpg"],
    number: 840,
    price: 9900,
    rating: 4,
    reviewsQuantity: 65,
  };
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .search-result {
    .block-default-styles();

    display: flex;
    flex-flow: column nowrap;
    // justify-content: space-between;

    &__content {
      margin-bottom: 40px;
    }

    &__title {
      .h1-text();

      margin-top: 0;
      margin-bottom: 0.875em;
    }

    &__grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
      justify-content: center;
      grid-gap: 20px 12px;
    }

    &__pagination {
      display: flex;
      justify-content: center;
      margin-top: auto;
    }
  }
</style>

<div class="search-result">
  <div class="search-result__content">
      <h2 class="search-result__title">Номера, которые мы для вас подобрали</h2>
      <div class="search-result__grid">
        {#each items as item}
          <div class="search-result__item">
            <RoomBox {...room888Options} />
          </div>
        {/each}
      </div>
  </div>
  <div class="search-result__pagination">
    <Pagination />
  </div>
</div>
