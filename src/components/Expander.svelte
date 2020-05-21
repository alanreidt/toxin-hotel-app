<script>
  let isExpanded = false;

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

    &_is-expanded &__trigger {
      color: #colors[dark-shade-75];
    }

    &__trigger {
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
