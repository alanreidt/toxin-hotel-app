<script>
  import flatpickr from "flatpickr";
  import "../../node_modules/flatpickr/dist/l10n/ru.js"

  const datepickerOptions = {
    locale: "ru",
    mode: "range",
    altInput: true,
    altFormat: "d.m.Y",
    allowInput: true,
    minDate: "today",
    // maxDate: new Date().fp_incr(2),
    // plugins: [new rangePlugin({ input: "#secondRangeInput"})],
    inline: true,
    // ariaDateFormat: "",
    // appendTo: HTMLElement,
    // disableMobile: Boolean,
    // nextArrow: String,
    // prevArrow: String,

    // showOtherMonths: true,
    // selectOtherMonths: true,
    // prevText: "",
    // nextText: "",
    // showButtonPanel: true,
    // closeText: "Применить",
    // currentText: "Очистить",
  };

  function datepickerInit(node, options = {}) {
    const flatpickrInstance = flatpickr(node, options);

    return {
      // update: (newOptions) => jQuery(node).datepicker("option", newOptions),
      destroy: () => flatpickrInstance.destroy(),
    };
  };
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .datepicker {
    position: relative;
    z-index: 100;
  }
</style>

<div use:datepickerInit={datepickerOptions} class="datepicker"></div>
