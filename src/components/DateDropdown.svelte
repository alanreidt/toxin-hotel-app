<script>
  import Expander from "./Expander.svelte";
  import DateInputField from "./DateInputField.svelte";
  import Datepicker from "./Datepicker.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .date-dropdown {
    display: flex;
    flex-flow: row wrap;

    @media (max-width: 380px - 4px + 2 * @site-paddings[small]) {
      flex-flow: column nowrap;
    }

    &__col {
      flex: 1 0 0;
      margin-right: 15px;

      @media (max-width: 380px - 4px + 2 * @site-paddings[small]) {
        margin-right: 0;
        margin-bottom: 10px;

        &:last-child {
          margin-bottom: 0;
        }
      }

      &:last-child {
        margin-right: 0;
      }
    }
  }
</style>

<Expander>
  <div class="date-dropdown" slot="trigger">
    <div class="date-dropdown__col">
      <DateInputField labelText="date dropdown" />
    </div>
    <div class="date-dropdown__col">
      <DateInputField labelText="date dropdown" />
    </div>
  </div>
  <div slot="menu">
    <Datepicker/>
  </div>
</Expander>
