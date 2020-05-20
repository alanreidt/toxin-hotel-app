<script>
  import InputField from "./InputField.svelte";

  import Cleave from "cleave.js";
  import { onMount } from "svelte";

  let inputField;

  const now = new Date();
  const nowISOString = now.toISOString();
  const afterTwoYearsFromNow = new Date(
    now.getFullYear() + 2,
    now.getMonth(),
    now.getDate()
  );
  const afterTwoYearsFromNowISOString = afterTwoYearsFromNow.toISOString();

  export let dateMin = nowISOString;
  export let dateMax = afterTwoYearsFromNowISOString;

  // I use onMount here, 'cause a use directive can't be attached to a component
  // You can pass an action property as alternative, but it'll restrict your options
  onMount(() => {
    const cleave = new Cleave(inputField, {
      date: true,
      delimiter: ".",
      dateMin,
      dateMax,
      datePattern: ["d", "m", "Y"],
    });

    return () => cleave.destroy();
  });
</script>

<InputField bind:inputField placeholder="ДД.ММ.ГГГГ" {...$$restProps} />
