<script>
  import RoomBoxCarousel from "./RoomBoxCarousel.svelte";
  import RoomInfo from "./RoomInfo.svelte";
  import RoomRating from "./RoomRating.svelte";

  export let imageSources;

  export let number;
  export let price;
  export let isLuxe;

  export let rating;
  export let reviewsQuantity;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-box {
    display: block;
    width: 100%;
    max-width: 270px;

    background-color: #fff;
    border-radius: 4px;
    box-shadow: 0 10px 20px rgba(31, 32, 65, 0.05);

    // prevent border-radius overlaping by child elements
    overflow: hidden;

    box-sizing: border-box;

    &__row {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__content {
      padding: 20px;
    }

    &__room-info {
      padding-bottom: 10px;

      border-bottom: 1px solid #colors[dark-shade-10];
    }

    &__room-rating {
      padding-top: 10px;
    }
  }
</style>

<div class="room-box">
  <div class="room-box__carousel">
    <RoomBoxCarousel {imageSources} />
  </div>
  <div class="room-box__content">
    <div class="room-box__room-info">
      <RoomInfo {number} {price} {isLuxe} />
    </div>
    <div class="room-box__room-rating">
      <RoomRating {rating} {reviewsQuantity} name="room-rating-{number}" />
    </div>
  </div>
</div>
