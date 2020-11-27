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

      height: 500px;

      @media (max-width: 1050px) {
        grid-template-areas:
        "a a a b b"
        "a a a c c";
        grid-gap: 5px;

        height: 450px;
      }

      @media (max-width: 780px) {
        grid-template-areas:
        "a a"
        "a a"
        "a a"
        "b c"
        "b c";
      }

      @media (max-width: 430px) {
        display: none;
      }
    }

    &__image {
      display: inline-block;
      vertical-align: top;

      width: 100%;
      height: 100%;

      object-fit: cover;
    }

    &__image:first-child {
      grid-area: a;
    }

    &__image:nth-child(2) {
      grid-area: b;
    }

    &__image:nth-child(3) {
      grid-area: c;
    }

    &__carousel {
      display: none;
      height: 240px;

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
          <img {src} class="room-details-head__image" />
        {/each}
      </div>
      <div class="room-details-head__carousel">
        <Carousel {imageSources} />
      </div>
    </div>
  </div>
</div>
