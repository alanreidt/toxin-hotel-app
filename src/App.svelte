<script>
  import InputField from "./components/InputField.svelte";
  import DateInputField from "./components/DateInputField.svelte";
  import Dropdown from "./components/Dropdown.svelte";
  import Button from "./components/Button.svelte";
</script>

<style>
  .row {
    max-width: 320px;
  }
</style>

<main>
  <div class="row">
    <InputField name="text-field" labelText="text field" placeholder="Email" />
    <DateInputField name="date-text-field" labelText="masked text field" />
    <Button text="click me" mods="main" href="#" />
    <Button text="click me" mods="secondary" href="#" />
    <Button text="click me" href="#" />
    <Button text="click me" mods="reset" href="#" />
    <Button text="перейти к оплате" mods="full-width" />
  </div>
</main>
