<script>
  import Expander from "./Expander.svelte";
  import InputField from "./InputField.svelte";
  import DropdownMenu from "./DropdownMenu.svelte";

  export let labelText;
  export let options;
  export let hasButtonPane;

  $: inputValue = composeString(options) || "Сколько гостей";

  function composeString(options) {
    const guestsQuantity = options[0].value + options[1].value;
    const guestsStr = `${guestsQuantity} ${
      guestsQuantity === 1 ? "гость" : "гостя"
    }`;
    const babiesQuantity = options[2].value;
    const babiesStr = `${babiesQuantity} ${
      babiesQuantity === 1 ? "младенец" : "младенца"
    }`;

    return [guestsStr, babiesStr]
      .filter((item) => Number(item[0]) !== 0)
      .join(", ");
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";
</style>

<Expander>
  <div on:focusin|stopPropagation slot="trigger">
    <InputField
      value={inputValue}
      readonly={true}
      {labelText}
      {...$$restProps} />
  </div>
  <div slot="menu">
    <DropdownMenu bind:options {hasButtonPane} />
  </div>
</Expander>
