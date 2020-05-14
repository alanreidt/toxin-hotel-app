<script>
  import DateInputField from "./DateInputField.svelte";
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

<div class="date-dropdown">
  <div class="date-dropdown__col">
    <DateInputField labelText="date dropdown" />
  </div>
  <div class="date-dropdown__col">
    <DateInputField labelText="date dropdown" />
  </div>
</div>
