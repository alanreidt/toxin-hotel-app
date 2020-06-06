<script>
  export let text;
  export let mods;
  export let isInput;

  // список модификаторов
  let allMods = "";

  if (typeof mods !== "undefined" && mods) {
    let modsList = mods.split(",");

    for (let i = 0; i < modsList.length; i++) {
      allMods = allMods + " button_" + modsList[i].trim();
    }
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @button-height: 44px;
  @button-border-width: 2px;

  .button {
    .not-selectable();
    .h3-text();

    // reset <button>, <input> styles
    padding: 0;
    border: none;
    background-color: transparent;

    // reset <a> styles
    text-decoration: none;

    // add compatibility between html elements (<a>, <button>, <input>)
    cursor: pointer;

    // add standart behaviour of a <button> to compatibility with <a>
    // isolate component's rules from external influence
    display: inline-block;
    vertical-align: middle;

    // add standart behaviour of a <button> to compatibility with <a>
    // isolate component's rules from external influence
    box-sizing: border-box;

    color: #colors[primary];
    text-align: center;
    text-overflow: ellipsis;
    overflow: hidden;

    &:hover,
    &:focus {
      opacity: 0.5;
    }

    &_reset {
      color: #colors[dark-shade-50];
    }

    &_secondary {
      .button_main();

      // using substraction because of box-sizing: border-box
      // now line-heigth equal to the content size of the button
      line-height: @button-height - 2 * @button-border-width;

      color: #colors[primary];
      background-image: none;
      background-color: #fff;
      border: @button-border-width solid #colors[primary];

      &:hover,
      &:focus {
        // border: 2px solid lighten(#colors[primary], 50%);
      }
    }

    &_full-width {
      .button_main();
      .decoration_type_arrow-forward();

      width: 100%;
    }
  }

  .button_main {
    height: @button-height;
    padding-left: 20px;
    padding-right: 20px;

    border-radius: 22px;

    // probably, sets value to 1.2 (or 1.15, depending on browser (user agent))
    // doesn't work with <a>, but work with <button>,
    // because text in a <button> aligns in the middle
    // line-height: normal;
    line-height: @button-height;
    color: #fff;
    background-image: @primary-gradient;
  }
</style>

<!-- - передан href — это ссылка -->
{#if $$props.href}
  <a class="button {allMods}" {...$$restProps}>
    {text}
    <slot />
  </a>

  <!-- - иначе, если передан isInput и он true, это input -->
{:else if isInput}
  <input class="button {allMods}" value={text} type="button" {...$$restProps} />

  <!-- - иначе это button -->
{:else}
  <button on:click class="button {allMods}" {...$$restProps}>
    {text}
    <slot />
  </button>
{/if}
