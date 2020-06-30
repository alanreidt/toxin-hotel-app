<script>
  import ToplineNav from "./ToplineNav.svelte";
  import Entrance from "./Entrance.svelte";

  export let userName;
  export let currentPageHref;
  export let optionsList;
  export let active = false;
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .topline-reception {
    background-color: #fff;

    @media (max-width: 1050px) {
      position: fixed;
      z-index: 800;
      top: 0;
      right: 0;

      display: flex;
      width: 40vw;
      min-width: 260px;
      height: 100%;

      box-shadow: 0 0 25px rgba(0, 0, 0, 0.2);

      opacity: 0;
      pointer-events: none;

      transform: translate3d(100%, 0, 0);
      overflow: auto;

      transition: transform 0.3s cubic-bezier(0.6, 0, 0, 1), opacity 0.3s ease;
      will-change: transform, opacity;

      &_active {
        opacity: 1;
        pointer-events: auto;

        transform: translate3d(0, 0, 0);
      }
    }

    @media (max-width: 500px) {
      width: 100%;
    }

    &__inner {
      .block-default-styles();

      display: flex;
      flex-flow: row nowrap;
      align-items: center;

      @media (max-width: 1050px) {
        flex-flow: column nowrap;
        justify-content: center;
        align-items: stretch;

        // make block to retain the height
        // when overflowed
        // (height: 100% and align-items: center (on parent)
        // break that behaviour)
        height: auto;
        margin: auto;

        padding-top: 40px;
        padding-bottom: 40px;
      }
    }

    &__entrance {
      margin-left: 15px;

      @media (max-width: 1050px) {
        margin-left: 0;
        margin-top: 20px;
      }
    }
  }
</style>

<div class="topline-reception {active ? 'topline-reception_active' : ''}">
  <div class="topline-reception__inner">
    <div class="topline-reception__topline-nav">
      <ToplineNav {optionsList} {currentPageHref} />
    </div>
    <div class="topline-reception__entrance">
      <Entrance {userName} />
    </div>
  </div>
</div>
