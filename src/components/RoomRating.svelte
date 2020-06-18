<script>
  import Rating from "./Rating.svelte";

  export let name;
  export let rating;
  export let reviewsQuantity;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-rating {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    &__reviews {
      .body-text();

      line-height: 1.29;
      color: #colors[dark-shade-50];
    }

    &__digit {
      font-weight: 700;
    }
  }
</style>

<div class="room-rating">
  <Rating id={name} {name} {rating} />

  <span class="room-rating__reviews">
    <span class="room-rating__digit">{reviewsQuantity}</span>
    Отзывов
  </span>
</div>
