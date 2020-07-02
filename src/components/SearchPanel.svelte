<script>
  import FilterDateDropdown from "./FilterDateDropdown.svelte";
  import Dropdown from "./Dropdown.svelte";
  import RangeSlider from "./RangeSlider.svelte";
  import Checkbox from "./Checkbox.svelte";
  import ExpandableCheckboxList from "./ExpandableCheckboxList.svelte";

  const guests = [
    { name: "Взрослые", min: 0, max: 5, value: 0 },
    { name: "Дети", min: 0, max: 5, value: 0 },
    { name: "Младенцы", min: 0, max: 3, value: 0 },
  ];

  const preferences = [
    { name: "Спальни", min: 1, max: 3, value: 0 },
    { name: "Кровати", min: 1, max: 3, value: 0 },
    { name: "Ванные комнаты", min: 1, max: 3, value: 0 },
  ];

  const permissions = [
    {
      labelText: "Можно курить",
      value: "smoke",
    },
    {
      labelText: "Можно с&nbsp;питомцами",
      value: "pets",
    },
    {
      labelText: "Можно пригласить гостей (до&nbsp;10&nbsp;человек)",
      value: "guests",
    },
  ];

  const accesibilityPreferences = [
    {
      labelText: "Широкий коридор",
      labelExplanation:
        "Ширина коридоров в&nbsp;номере не&nbsp;менее 91&nbsp;см.",
      value: "wide-corridor",
    },
    {
      labelText: "Помощник для инвалидов",
      labelExplanation:
        "На&nbsp;1&nbsp;этаже вас встретит специалист и&nbsp;проводит до&nbsp;номера.",
      value: "assistant",
    },
  ];

  const additionalPreferences = [
    {
      labelText: 'Завтрак',
      value: 'breakfast',
    },
    {
      labelText: 'Письменный стол',
      value: 'desk',
    },
    {
      labelText: 'Стул для кормления',
      value: 'feeding-chair',
    },
    {
      labelText: 'Телевизор',
      value: 'TV',
    },
    {
      labelText: 'Шампунь',
      value: 'shampoo',
    },
  ];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .search-panel {
    .block-default-styles();

    background-color: #fff;

    &__row {
      margin-bottom: 30px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__item {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__input-text {
      #box.input-text();

      &_for_checkbox {
        margin-bottom: 16px;
      }
    }

    &__fieldset {
      .fieldset-styles-reset();
    }
  }
</style>

<div class="search-panel">
  <form name="search-panel-form" autocomplete="on">
      <div class="search-panel__row">
          <div class="search-panel__item">
            <FilterDateDropdown />
          </div>

          <div class="search-panel__item">
            <Dropdown
              options={guests}
              name="guests" />
          </div>
      </div>

      <div class="search-panel__row">
        <RangeSlider />
      </div>

      <div class="search-panel__row">
        <span class="search-panel__input-text search-panel__input-text_for_checkbox">Позволения номера</span>
        <fieldset class="search-panel__fieldset">
          {#each permissions as option}
            <Checkbox {...option} name="permissions" />
          {/each}
        </fieldset>
      </div>

      <div class="search-panel__row">
        <span class="search-panel__input-text search-panel__input-text_for_checkbox">Доступность</span>
        <fieldset class="search-panel__fieldset">
          {#each accesibilityPreferences as option}
            <Checkbox {...option} name="accesibility" />
          {/each}
        </fieldset>
      </div>

      <div class="search-panel__row">
        <Dropdown
        labelText="Удобства номера"
        options={preferences}
        name="preferences" />
      </div>

      <div class="search-panel__row">
        <ExpandableCheckboxList
          options={additionalPreferences}
          name="additional-preferences" />
      </div>
  </form>
</div>
