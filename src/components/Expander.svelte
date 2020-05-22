<script>
  export let isExpanded = false;

  function handleExpanderFocusin() {
    isExpanded = true;
  }

  function handleExpanderFocusout() {
    isExpanded = false;
  }

  function toggleIsExpanded() {
    isExpanded = !isExpanded;
  }

  const SPACE_KEY = " ";

  function handleTriggerKeydown(event) {
    if (event.key === "Enter" || event.key === SPACE_KEY) {
      event.preventDefault();

      toggleIsExpanded();
    }

    if (event.key === "Escape" || event.key === "Esc") {
      event.preventDefault();

      isExpanded = false;
    }
  }

  function handleTriggerClick() {
    toggleIsExpanded();
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .expander {
    position: relative;
    z-index: 200;

    display: inline-block;
    vertical-align: middle;
    width: 100%;

    &_is-expanded &__menu {
      pointer-events: auto;
      opacity: 1;
    }

    &__menu {
      position: absolute;
      z-index: 200;
      width: 100%;
      top: 100%;
      left: 0;

      opacity: 0;
      pointer-events: none;
    }
  }
</style>

<div
  on:focusin={handleExpanderFocusin}
  on:focusout={handleExpanderFocusout}
  class="expander {isExpanded ? 'expander_is-expanded' : ''}">
  <div
    class="expander__trigger"
    on:keydown={handleTriggerKeydown}
    on:click={handleTriggerClick}>
    <slot name="trigger" />
  </div>
  <div class="expander__menu">
    <slot name="menu" />
  </div>
</div>
