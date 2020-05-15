<script>
  import Rating from "./Rating.svelte";
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
  <Rating id='room-box-rating' name='room-box-rating' />

  <span class="room-rating__reviews">
    <span class="room-rating__digit">145</span>
    Отзывов
  </span>
</div>
