<script>
  import Hero from "../components/Hero.svelte";

  import { metatags } from '@sveltech/routify';

  metatags.title = "Лучшие номера для вашей работы, отдыха и просто вдохновения";
  metatags.description = "Change me";
</script>

<!-- routify:options name="index" index=false -->

<Hero />
