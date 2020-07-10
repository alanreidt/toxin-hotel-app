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

    &__content {
      .block-default-styles();

      display: grid;
      /* grid-template-columns: 2fr 1fr; */
      grid-template-areas:
      "a a b"
      "a a c";
      grid-gap: 10px;
      justify-content: space-between;
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
  }
</style>

<div class="room-details-head">
  <div class="room-details-head__container">
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
</div>
