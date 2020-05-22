<script>
  import Expander from "./Expander.svelte";
  import DateInputField from "./DateInputField.svelte";
  import Datepicker from "./Datepicker.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .date-dropdown {
    &__input-group {
      display: flex;
      flex-flow: row wrap;

      @media (max-width: 380px - 4px + 2 * @site-paddings[small]) {
        flex-flow: column nowrap;
      }
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

    &__input {
      position: relative;
      color: #colors[dark-shade-50];

      &::after {
        .material-icons();
        font-size: 1.5rem;

        content: "\e5cf";
        position: absolute;
        bottom: 0;
        right: 0;

        display: inline-block;
        vertical-align: middle;

        width: 2.75rem;
        height: 2.75rem;
        line-height: 2.75rem;

        text-align: center;
        color: inherit;
        background-color: transparent;

        box-sizing: border-box;
        pointer-events: none;
      }
    }

    &__datepicker {
      padding-top: 5px;
    }
  }
</style>

<div class="date-dropdown">
  <Expander>
    <div on:keydown|stopPropagation on:click|stopPropagation class="date-dropdown__input-group" slot="trigger">
      <div class="date-dropdown__col date-dropdown__input">
        <DateInputField class="date-dropdown__input" labelText="date dropdown" />
      </div>
      <div class="date-dropdown__col date-dropdown__input">
        <DateInputField class="date-dropdown__input" labelText="date dropdown" />
      </div>
    </div>
    <div class="date-dropdown__datepicker" slot="menu">
      <Datepicker/>
    </div>
  </Expander>
</div>
