<script>
  export let isExpanded = false;
  let expander;

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

  document.addEventListener("click", (event) => {
    const isExpanderTarget = event.target.closest(".expander") === expander;

    if (isExpanderTarget) return;

    isExpanded = false;
  }, true);

  document.addEventListener("focusin", (event) => {
    const isExpanderTarget = event.target.closest(".expander") === expander;

    if (isExpanderTarget) return;

    isExpanded = false;
  }, true);
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .expander {
    position: relative;

    display: inline-block;
    vertical-align: top;
    width: 100%;

    &_is-expanded &__menu {
      visibility: inherit;
    }

    &__menu {
      position: absolute;
      z-index: 200;
      width: 100%;
      top: 100%;
      left: 0;

      visibility: hidden;
    }
  }
</style>

<div
  bind:this={expander}
  class="expander {isExpanded ? 'expander_is-expanded' : ''}">
  <div
    class="expander__trigger"
    on:focusin={handleExpanderFocusin}
    on:keydown={handleTriggerKeydown}
    on:click={handleTriggerClick}>
    <slot name="trigger" />
  </div>
  <div class="expander__menu">
    <slot name="menu" />
  </div>
</div>
