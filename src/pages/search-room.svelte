<script>
  import Search from "../components/Search.svelte";

  import { metatags } from '@sveltech/routify';

  metatags.title = "Найдите номер под ваши желания";
  metatags.description = "Change me";
</script>

<!-- routify:options name="search-room" index=false -->

<Search />
