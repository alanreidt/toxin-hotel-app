<script>
  import DateInputField from "./DateInputField.svelte";
  import { onMount } from "svelte";

  import flatpickr from "flatpickr";
  import rangePlugin from "../../node_modules/flatpickr/dist/plugins/rangePlugin";
  import "../../node_modules/flatpickr/dist/l10n/ru.js";

  export let startDateLabelText = "Прибытие";
  export let endDateLabelText = "Выезд";

  let startDateInputField;
  let endDateInputField;

  // I use onMount here, 'cause a use directive can't be attached to a component
  // You can pass an action property as alternative, but it'll restrict your options
  onMount(() => {
    const datepickerOptions = {
      locale: "ru",
      mode: "range",
      // altInput: true,
      // altFormat: "d.m.Y",
      // defaultDate: ["10.06.2020", "17.06.2020"],
      dateFormat: "d.m.Y",
      allowInput: true,
      minDate: "today",
      // maxDate: new Date().fp_incr(2),
      plugins: [new rangePlugin({ input: endDateInputField})],
      // inline: true,
      // ariaDateFormat: "",
      // appendTo: HTMLElement,
      // disableMobile: Boolean,
      nextArrow: "",
      prevArrow: "",
    };

    const flatpickrInstance = flatpickr(startDateInputField, datepickerOptions);

    return () => flatpickrInstance.destroy();
  });
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
  }
</style>

<div class="date-dropdown">
  <div class="date-dropdown__input-group">
    <div class="date-dropdown__col date-dropdown__input">
      <DateInputField bind:inputField={startDateInputField} labelText={startDateLabelText} />
    </div>
    <div class="date-dropdown__col date-dropdown__input">
      <DateInputField bind:inputField={endDateInputField} labelText={endDateLabelText} />
    </div>
  </div>
</div>
