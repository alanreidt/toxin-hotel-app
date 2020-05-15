<script>
  import RoomInfo from "./RoomInfo.svelte";
  import DateDropdown from "./DateDropdown.svelte";
  import Dropdown from "./Dropdown.svelte";
  import Button from "./Button.svelte";

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
    #box();

    &__inner {
      #box.inner();
    }

    & .datepicker {
      // lay out above .calculation-box__service-text
      z-index: 200;
    }

    &__row {
      #box.row();
    }

    &__item {
      #box.item();
    }

    &__input-text {
      #box.input-text();
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
  <div class="calculation-box__inner">
    <div class="calculation-box__row">
      <RoomInfo number='888' price='9 990₽' isLuxe={true}/>
    </div>
    <form name="calculation-box-form" autocomplete="on">
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
            <span class="calculation-box__service-text">9 990₽ x 4 суток</span>
            <span class="calculation-box__service-price">39 960₽</span>
          </div>
        </div>
        <div class="calculation-box__item">
          <div class="calculation-box__service-info">
            <span class="calculation-box__service-text">
              Сбор за услуги: скидка 2 179₽
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
              Сбор за дополнительные услуги
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
      <div class="calculation-box__row">
        <div class="calculation-box__item calculation-box__summary-group">
          <div class="calculation-box__summary-info">
            <span class="calculation-box__summary-text">Итого</span>
            <span class="calculation-box__summary-price">38 081₽</span>
          </div>
        </div>
        <div class="calculation-box__item">
          <Button text="Забронировать" mods="full-width" />
        </div>
      </div>
    </form>
  </div>
</div>
