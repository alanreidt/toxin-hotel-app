<script>
  import RoomDetailsContent from "./RoomDetailsContent.svelte";
  import CalculationBox from "./CalculationBox.svelte";

  const calculationBoxOptions = {
    number: 888,
    price: 9990,
    isLuxe: true,
  };
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-details-body {
    .block-default-styles();

    background-color: #fff;

    &__container {
      .container();
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
      align-items: flex-start;

      padding-top: 70px;
      padding-bottom: 70px;
    }

    &__room-details-content {
      flex: 1 1 0;
    }

    &__calculation-box {
      flex: 1 1 0;
      max-width: 380px;

      box-sizing: border-box;
    }
  }
</style>

<div class="room-details-body">
  <div class="room-details-body__container">
    <div class="room-details-body__inner">
      <div class="room-details-body__room-details-content">
        <RoomDetailsContent />
      </div>
      <div class="room-details-body__calculation-box">
        <CalculationBox {...calculationBoxOptions} />
      </div>
    </div>
  </div>
</div>
