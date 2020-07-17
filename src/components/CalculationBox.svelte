<script>
  import Box from "./Box.svelte";
  import RoomInfo from "./RoomInfo.svelte";
  import DateDropdown from "./DateDropdown.svelte";
  import Dropdown from "./Dropdown.svelte";
  import Button from "./Button.svelte";

  export let number;
  export let price;
  export let isLuxe;

  const dropdownOptions = [
    { name: "Взрослые", min: 0, max: 5, value: 0 },
    { name: "Дети", min: 0, max: 5, value: 0 },
    { name: "Младенцы", min: 0, max: 3, value: 0 },
  ];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .calculation-box {
    &__row {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__item {
      #box.item();
    }

    &__service-info {
      #box.space-between();
      .body-text();

      align-items: flex-start;
    }

    &__service-text {
      position: relative;
      z-index: 100;

      width: 100%;
      max-width: 240px;
      padding-right: 25px;

      box-sizing: border-box;
    }

    &__icon-info {
      position: absolute;
      z-index: 200;
      top: 0;
      right: 0;

      font-size: 20px;
      color: #colors[dark-shade-25];

      cursor: pointer;
    }

    &__summary-group {
      margin-bottom: 20px;
    }

    &__summary-info {
      #box.space-between();
      .h2-text();

      align-items: flex-start;

      line-height: 0.7;
      border-bottom: 1px dotted #colors[dark-shade-25];
    }

    &__summary-text {
      padding-right: 5px;
      margin-bottom: -1px;
      background-color: #fff;
    }

    &__summary-price {
      padding-left: 5px;
      margin-bottom: -1px;
      background-color: #fff;
    }
  }
</style>

<div class="calculation-box">
  <form name="calculation-box-form" autocomplete="on">
    <Box>
      <div slot="title" class="calculation-box__header">
        <RoomInfo {number} {price} {isLuxe} />
      </div>

      <div class="calculation-box__row">
        <DateDropdown/>
      </div>
      <div class="calculation-box__row">
      <Dropdown
        labelText="Гости"
        options={dropdownOptions}
        hasButtonPane={true}
        name="guests"
        required />
      </div>
      <div class="calculation-box__row">
        <div class="calculation-box__item">
          <div class="calculation-box__service-info">
            <span class="calculation-box__service-text">9 990₽ x&nbsp;4&nbsp;суток</span>
            <span class="calculation-box__service-price">39 960₽</span>
          </div>
        </div>
        <div class="calculation-box__item">
          <div class="calculation-box__service-info">
            <span class="calculation-box__service-text">
              Сбор за&nbsp;услуги: скидка 2 179₽
              <i
                class="material-icons calculation-box__icon-info"
                title="change me — use jQuery">
                info_outline
              </i>
            </span>
            <span class="calculation-box__service-price">0₽</span>
          </div>
        </div>
        <div class="calculation-box__item">
          <div class="calculation-box__service-info">
            <span class="calculation-box__service-text">
              Сбор за&nbsp;дополнительные услуги
              <i
                class="material-icons calculation-box__icon-info"
                title="change me — use jQuery">
                info_outline
              </i>
            </span>
            <span class="calculation-box__service-price">300₽</span>
          </div>
        </div>
      </div>

      <div slot="footer" class="calculation-box__footer">
        <div class="calculation-box__row">
          <div class="calculation-box__summary-info">
            <span class="calculation-box__summary-text">Итого</span>
            <span class="calculation-box__summary-price">38 081₽</span>
          </div>
        </div>
        <div class="calculation-box__row">
          <Button text="Забронировать" mods="full-width" />
        </div>
      </div>
    </Box>
  </form>
</div>
