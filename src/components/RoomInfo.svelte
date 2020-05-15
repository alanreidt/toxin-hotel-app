<script>
  export let number;
  export let price;
  export let isLuxe;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-info {
    #box.space-between();

    align-items: flex-end;

    &__details {
      .h2-text();

      font-size: 14px;
      line-height: 1.214; /* 17px = 14px * 1.214 */
    }

    &__digit {
      font-size: 24px;
      margin-right: 5px;
      margin-left: 3px;
    }

    &__rank {
      .h3-text();

      color: #colors[primary];
    }

    &__price {
      .body-text();

      line-height: 1.29;
      font-weight: bold;
      color: #colors[dark-shade-50];
    }

    &__text {
      font-size: 12px;
      font-weight: normal;
    }
  }
</style>

<div class="room-info">
  <span class="room-info__details">
    №
    <span class="room-info__digit">{number}</span>
    {#if isLuxe}
      <span class="room-info__rank">люкс</span>
    {/if}
  </span>
  <span class="room-info__price">
    {price}
    <span class="room-info__text">в сутки</span>
  </span>
</div>
