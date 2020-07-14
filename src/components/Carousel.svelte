<script>
  import Carousel from "@beyonk/svelte-carousel";

  export let imageSources = [];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .carousel {
    display: block;
    vertical-align: middle;
    width: 100%;

    &__item {
      display: block;
      width: 100%;
    }

    &__image {
      display: inline-block;
      vertical-align: middle;
      width: auto;
      max-width: 100%;
    }

    & :global(button) {
      top: 0;
      width: 42px;
      height: 100%;
      margin-top: 0;
      padding: 0;
    }

    & :global(.left) {
      left: 0;
    }

    & :global(.right) {
      right: 0;
    }

    &:hover &__lever,
    &:focus &__lever {
      opacity: 1;
    }

    &__lever {
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;

      width: 100%;
      height: 100%;

      background-color: transparent;
      color: #fff;

      background-image: linear-gradient(
        90deg,
        rgba(0, 0, 0, 0.5) 0%,
        rgba(0, 0, 0, 0) 99.99%,
        rgba(255, 255, 255, 0) 100%
      );

      cursor: pointer;
      opacity: 0;

      transition: 0.15s ease-out;

      &_next {
        transform: matrix(-1, 0, 0, 1, 0, 0);
      }
    }

    & :global(ul) {
      margin-top: 0;
      margin-bottom: 0;
      padding-left: 0;

      position: absolute;
      /* z-index: 200; */
      bottom: 15px;
      right: 15px;

      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      /* align-items: unset; */
      width: auto;

      background-color: transparent;
    }

    & :global(ul li) {
      list-style-type: none;

      margin: 0;
      margin-right: 4px;

      /* text-decoration: none; */

      display: block;
      width: 8px;
      height: 8px;

      background-color: transparent;
      border: 1px solid #fff;
      border-radius: 50%;
      box-shadow: 0 5px 5px rgba(31, 32, 65, 0.3);

      cursor: pointer;
      box-sizing: border-box;

      &.active {
        background-color: #fff;
      }

      &:last-child {
        margin-right: 0;
      }
    }
  }
</style>

<div class="carousel">
  <Carousel perPage="1">
    <div class="carousel__lever" slot="left-control">
      <i class="material-icons">navigate_before</i>
    </div>
    <div class="carousel__lever carousel__lever_next" slot="right-control">
      <i class="material-icons">navigate_before</i>
    </div>
    {#each imageSources as src}
      <div class="carousel__item">
        <img {src} alt="room photo" class="carousel__image">
      </div>
    {/each}
  </Carousel>
</div>
