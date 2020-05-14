<script>
  import InputField from "./components/InputField.svelte";
  import DateInputField from "./components/DateInputField.svelte";
  import Dropdown from "./components/Dropdown.svelte";
  import DateDropdown from "./components/DateDropdown.svelte";
  import SubscriptionField from "./components/SubscriptionField.svelte";
  import Checkbox from "./components/Checkbox.svelte";
  import StatefulInput from "./components/StatefulInput.svelte";
  import Rating from "./components/Rating.svelte";
  import Button from "./components/Button.svelte";
  import DropdownMenu from "./components/DropdownMenu.svelte";

  const checkboxOptions = [
    {
      labelText: "Можно курить",
      value: "smoke",
    },
    {
      labelText: "Можно с&nbsp;питомцами",
      value: "pets",
    },
    {
      labelText: "Можно пригласить гостей (до&nbsp;10&nbsp;человек)",
      value: "guests",
    },
  ];

  const statefullInputOptions = [
    { labelText: "Мужчина", value: "man", checked: true },
    { labelText: "Женщина", value: "woman", checked: false },
  ];
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
      options={[{ name: 'Взрослые', min: 0, max: 5, value: 0 }, { name: 'Дети', min: 0, max: 5, value: 0 }, { name: 'Младенцы', min: 0, max: 3, value: 0 }]}
      hasButtonPane={true}
      name="dropdown-input" />
    <DateDropdown />
    <SubscriptionField labelText="subscription text field" />
    {#each checkboxOptions as option}
      <Checkbox {...option} name="permission" />
    {/each}
    {#each statefullInputOptions as option}
      <StatefulInput {...option} type="radio" name="sex" />
    {/each}
    <StatefulInput
      labelText="Получать спецпредложения"
      mods="type_toggle"
      type="checkbox"
      name="mailing"
      value="on" />
    <StatefulInput
      labelText="Нравится"
      mods="type_like-button"
      type="checkbox"
      name="like-button"
      value="on" />
    <Rating id="rating" name="rating" />

    <Button text="click me" mods="main" href="#" />
    <Button text="click me" mods="secondary" href="#" />
    <Button text="click me" href="#" />
    <Button text="click me" mods="reset" href="#" />
    <Button text="перейти к оплате" mods="full-width" />
  </div>
</main>
