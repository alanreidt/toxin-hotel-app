<script>
  import InputField from './components/InputField.svelte';
  import DateInputField from './components/DateInputField.svelte';
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
  </div>
</main>
