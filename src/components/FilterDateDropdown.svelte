<script>
  import InputField from "./InputField.svelte";
  import { onMount } from "svelte";

  import flatpickr from "flatpickr";
  import "../../node_modules/flatpickr/dist/l10n/ru.js";

  let inputField;

  // I use onMount here, 'cause a use directive can't be attached to a component
  // You can pass an action property as alternative, but it'll restrict your options
  onMount(() => {
    const datepickerOptions = {
      locale: "ru",
      mode: "range",
      // altInput: true,
      // altFormat: "d.m.Y",
      dateFormat: "d M",
      minDate: "today",
      // maxDate: new Date().fp_incr(2),
      // inline: true,
      // ariaDateFormat: "",
      // appendTo: HTMLElement,
      // disableMobile: Boolean,
      nextArrow: "",
      prevArrow: "",
    };

    const flatpickrInstance = flatpickr(inputField, datepickerOptions);

    return () => flatpickrInstance.destroy();
  });
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .filter-date-dropdown {
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

<div class="filter-date-dropdown">
  <div class="filter-date-dropdown__input">
    <InputField bind:inputField labelText="filter date dropdown" placeholder="Выберите дату" />
  </div>
</div>
