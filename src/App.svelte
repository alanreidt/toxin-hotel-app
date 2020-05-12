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
    <Dropdown
      labelText="Dropdown"
      options={[
        {name: 'Взрослые', min: 0, max: 5, value: 0},
        {name: 'Дети', min: 0, max: 5, value: 0},
        {name: 'Младенцы', min: 0, max: 3, value: 0},
      ]}
      hasButtonPane={true}
      name="dropdown-input" />
    <Button text="click me" mods="main" href="#" />
    <Button text="click me" mods="secondary" href="#" />
    <Button text="click me" href="#" />
    <Button text="click me" mods="reset" href="#" />
    <Button text="перейти к оплате" mods="full-width" />
  </div>
</main>
