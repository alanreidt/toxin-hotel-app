<script>
  import InputField from './components/InputField.svelte';
</script>

<style>
  .row {
    max-width: 320px;
  }
</style>

<main>
  <div class="row">
    <InputField name="text-field" labelText="text field" placeholder="Email" />
  </div>
</main>
