<script>
  import Pagination from "./Pagination.svelte";
  import RoomBox from "./RoomBox.svelte";

  const rooms = [
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-888.jpg", "images/room-840.jpg"],
      number: 888,
      price: 9990,
      isLuxe: true,
      rating: 5,
      reviewsQuantity: 145,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-840.jpg"],
      number: 840,
      price: 9900,
      rating: 4,
      reviewsQuantity: 65,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-980.jpg"],
      number: 980,
      isLuxe: true,
      price: 8500,
      rating: 3,
      reviewsQuantity: 35,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-856.jpg"],
      number: 856,
      price: 7300,
      rating: 5,
      reviewsQuantity: 19,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-740.jpg"],
      number: 740,
      price: 6000,
      rating: 4,
      reviewsQuantity: 44,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-982.jpg"],
      number: 982,
      price: 5800,
      rating: 3,
      reviewsQuantity: 56,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-678.jpg"],
      number: 678,
      price: 5500,
      rating: 5,
      reviewsQuantity: 45,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-450.jpg"],
      number: 450,
      price: 5300,
      rating: 4,
      reviewsQuantity: 39,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-350.jpg"],
      number: 350,
      price: 5000,
      rating: 3,
      reviewsQuantity: 77,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-666.jpg"],
      number: 666,
      price: 5000,
      rating: 5,
      reviewsQuantity: 25,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-444.jpg"],
      number: 444,
      price: 5000,
      rating: 3,
      reviewsQuantity: 15,
    },
    {
      href: "/mock-address/change-me",
      imageSources: ["images/room-352.jpg"],
      number: 352,
      price: 5000,
      rating: 3,
      reviewsQuantity: 55,
    },
  ];
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
        {#each rooms as options}
          <div class="search-result__item">
            <RoomBox {...options} />
          </div>
        {/each}
      </div>
  </div>
  <div class="search-result__pagination">
    <Pagination />
  </div>
</div>
