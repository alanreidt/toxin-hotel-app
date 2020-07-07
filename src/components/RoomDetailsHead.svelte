<script>
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
    height: 33vw;

    @media (max-width: @site-width) {
      height: 35vw;
    }

    @media (max-width: 1050px) {
      height: 37vw;
    }

    @media (max-width: 833px) {
      height: 39vw;
    }

    @media (max-width: 760px) {
      height: 40vh;
      min-height: 340px;
    }

    @media (max-width: 540px) {
      height: 25vh;
      min-height: 200px;
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row nowrap;
      justify-content: flex-start;
      align-items: stretch;

      @media (max-width: 760px) {
        flex-flow: column nowrap;
      }

      @media (max-width: 540px) {
        flex-flow: row nowrap;
      }
    }

    &__image {
      display: inline-block;
      vertical-align: middle;
      width: auto;
      max-width: 100%;
    }
  }
</style>

<div class="room-details-head">
  <div class="room-details-head__inner">
    <div class="room-details-head__content">
      {#each imageSources as src}
        <div class="room-details-head__item">
          <img {src} class="room-details-head__image" />
        </div>
      {/each}
    </div>
  </div>
</div>
