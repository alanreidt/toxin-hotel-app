<script>
  import "../../node_modules/jquery-ui/ui/widgets/datepicker";

  const datepickerOptions = {
    showOtherMonths: true,
    selectOtherMonths: true,
    prevText: "",
    nextText: "",
    showButtonPanel: true,
    closeText: "Применить",
    currentText: "Очистить",
    minDate: 0,
  };

  function datepickerInit(node, options) {
    jQuery(node).datepicker(options);

    return {
      update: (newOptions) => jQuery(node).datepicker("option", newOptions),
      destroy: () => jQuery(node).datepicker("destroy"),
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
