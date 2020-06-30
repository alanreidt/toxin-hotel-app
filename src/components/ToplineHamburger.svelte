<script>
  export let active = false;

  function handleToplineHamburgerClick(event) {
    active = !active;
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .topline-hamburger {
    --topline-center: calc(
      (
          var(--topline-height) -
            (var(--menu-button-height) + 2 * var(--menu-button-padding))
        ) / 2
    );

    .not-selectable();

    // reset <button>, <input> styles
    border: none;
    background-color: transparent;

    text-overflow: ellipsis;
    overflow: hidden;

    display: none;
    padding: var(--menu-button-padding);

    cursor: pointer;
    box-sizing: border-box;

    @media (max-width: 1050px) {
      position: relative;
      z-index: 900;

      display: inline-block;
      vertical-align: middle;
    }

    &_active &__stripe:first-child {
      transform: translate3d(0, 6px, 0);
    }

    &_active &__stripe:nth-child(2) {
      transform: rotate(45deg);
    }

    &_active &__stripe:nth-child(3) {
      transform: rotate(-45deg);
    }

    &_active &__stripe:last-child {
      transform: translate3d(0, -6px, 0);
    }

    &_active &__stripe:nth-child(3n + 1) {
      opacity: 0;
    }

    &__icon {
      display: flex;
      flex-flow: column nowrap;
      justify-content: space-between;
      align-items: stretch;

      width: 20px;
      height: var(--menu-button-height);
    }

    &__stripe {
      display: inline-block;
      vertical-align: middle;
      height: 2px;

      background-color: #colors[dark-shade-50];

      transition: transform 0.15s cubic-bezier(0.6, 0, 0, 1),
        opacity 0s ease 50ms;
      will-change: transform, opacity;
    }

    &__stripe:nth-child(3) {
      // hide stripe behind prev one
      // the only alternative here is absolute positioning
      // but that approach is shorter
      margin-top: -6px;
    }
  }
</style>

<button
  on:click={handleToplineHamburgerClick}
  class="topline-hamburger {active ? 'topline-hamburger_active' : ''}"
  type="button"
  id="menu-button">
  <div class="topline-hamburger__icon">
    <span class="topline-hamburger__stripe"></span>
    <span class="topline-hamburger__stripe"></span>
    <span class="topline-hamburger__stripe"></span>
    <span class="topline-hamburger__stripe"></span>
  </div>
</button>
