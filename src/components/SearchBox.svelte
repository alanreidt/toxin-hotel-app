<script>
  import Box from "./Box.svelte";
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
    &__row {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__title {
      @media (max-width: 340px) {
        text-align: center;
      }
    }
  }
</style>

<div class="search-box">
  <form name="search-box-form" autocomplete="off">
    <Box>
      <span slot="title" class="search-box__title">Найдем номера под ваши пожелания</span>
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
      <div slot="footer" class="search-box__footer">
        <Button href="/mock-address/change-me" text="подобрать номер" mods="full-width" />
      </div>
    </Box>
  </form>
</div>
