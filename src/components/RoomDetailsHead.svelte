<script>
  import Carousel from "./Carousel.svelte";

  export let imageSources = [
    "/images/room-details-888.jpg",
    "/images/room-details-888-2.jpg",
    "/images/room-details-888-3.jpg",
  ];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-details-head {
    .block-default-styles();

    &__container {
      .container();

      @media (max-width: @site-width) {
        padding-left: 0;
        padding-right: 0;
      }
    }

    &__inner {
      .block-default-styles();
    }

    &__grid {
      .block-default-styles();

      display: grid;
      grid-template-areas:
      "a a b"
      "a a c";
      grid-gap: 10px;
      justify-content: space-between;

      @media (max-width: 1050px) {
        grid-gap: 5px;
        grid-template-areas:
        "a a a b b"
        "a a a c c";
      }

      @media (max-width: 780px) {
        grid-template-areas:
        "a a"
        "b c";
      }

      @media (max-width: 430px) {
        display: none;
      }
    }

    &__item {
      .block-default-styles();
    }

    &__item:first-child {
      grid-area: a;
    }

    &__item:nth-child(2) {
      grid-area: b;
    }

    &__item:nth-child(3) {
      grid-area: c;
    }

    &__image {
      display: inline-block;
      vertical-align: middle;
      width: auto;
      max-width: 100%;
      height: 100%;
      object-fit: cover;
    }

    &__carousel {
      display: none;

      @media (max-width: 430px) {
        display: block;
      }
    }
  }
</style>

<div class="room-details-head">
  <div class="room-details-head__container">
    <div class="room-details-head__inner">
      <div class="room-details-head__grid">
        {#each imageSources as src}
          <div class="room-details-head__item">
            <img {src} class="room-details-head__image" />
          </div>
        {/each}
      </div>
      <div class="room-details-head__carousel">
        <Carousel {imageSources} />
      </div>
    </div>
  </div>
</div>
