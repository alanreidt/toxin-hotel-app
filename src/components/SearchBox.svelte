<script>
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

  .search-box {
    #box();

    &__inner {
      #box.inner();
    }

    &__row {
      #box.row();
    }

    &__title {
      #box.title();

      @media (max-width: 340px) {
        text-align: center;
      }
    }

    &__input-text {
      #box.input-text();
    }
  }
</style>

<div class="search-box">
  <div class="search-box__inner">
    <div class="search-box__row">
      <h2 class="search-box__title">Найдем номера под ваши пожелания</h2>
    </div>
    <form name="search-box-form" autocomplete="off">
      <div class="search-box__row">
        <DateDropdown/>
      </div>
      <div class="search-box__row">
        <Dropdown
          labelText="Гости"
          options={dropdownOptions}
          hasButtonPane={true}
          name="guests" />
      </div>
      <div class="search-box__row">
        <Button href="/mock-address/change-me" text="перейти к оплате" mods="full-width" />
      </div>
    </form>
  </div>
</div>
