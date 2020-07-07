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

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();
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
  <div class="room-details-head__container">
    <div class="room-details-head__inner">
      <div class="room-details-head__content">
        {#each imageSources as src}
          <img {src} class="room-details-head__image" />
        {/each}
      </div>
    </div>
  </div>
</div>
