<script>
  import Expander from "./Expander.svelte";
  import Checkbox from "./Checkbox.svelte";

  let expanded = false;

  export let labelText ="Дополнительные удобства";
  export let options = [];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @button-height: 18px;

  .expandable-checkbox-list {
    display: block;
    width: 100%;

    &_expanded &__trigger::after {
      transform: rotate(-180deg);
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
        /* height: 2.75rem;
        line-height: 2.75rem; */
        height: @button-height;
        line-height: @button-height;

        text-align: center;
        color: inherit;
        background-color: transparent;

        transition: transform 0.3s ease;

        box-sizing: border-box;
        pointer-events: none;
      }
    }

    &__button {
      // reset <button>, <input> styles
      padding: 0;
      border: none;
      background-color: transparent;

      // reset <a> styles
      text-decoration: none;

      // add compatibility between html elements (<a>, <button>, <input>)
      cursor: pointer;

      // add standart behavior of a <button> to compatibility with <a>
      // isolate component's rules from external influence
      display: inline-block;
      vertical-align: top;
      width: 100%;

      .h3-text();
      .not-selectable();

      height: @button-height;
      text-align: left;
    }

    &__menu {
      .fieldset-styles-reset();

      padding-top: 18px;
      background-color: #fff;
    }
  }
</style>

<div class="expandable-checkbox-list {expanded ? 'expandable-checkbox-list_expanded' : ''}">
  <Expander bind:isExpanded={expanded}>
    <div on:focusin|stopPropagation slot="trigger" class="expandable-checkbox-list__trigger">
      <button type="button" class="expandable-checkbox-list__button">{labelText}</button>
    </div>
    <fieldset slot="menu" class="expandable-checkbox-list__menu">
      {#each options as option}
        <Checkbox {...option} {...$$restProps}/>
      {/each}
    </fieldset>
  </Expander>
</div>
