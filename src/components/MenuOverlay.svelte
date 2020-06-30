<script>
  export let active = false;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .menu-overlay {
    .block-default-styles();

    position: fixed;
    z-index: 700;
    top: 0;
    left: 0;

    background-color: rgba(0, 0, 0, 0.2);

    pointer-events: none;
    opacity: 0;

    transition: opacity 0.3s ease;
    will-change: opacity;

    &_active {
      pointer-events: auto;
      opacity: 1;
    }
  }
</style>

<div class="menu-overlay {active ? 'menu-overlay_active' : ''}" id="menu-overlay"></div>
