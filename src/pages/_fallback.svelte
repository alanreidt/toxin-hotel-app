<script>
    import { url } from '@sveltech/routify'
</script>

<style>
  .e404 {
    text-align: center;
  }

  .huge {
    font-size: 12rem;
  }

  .big {
    font-size: 2rem;
  }
</style>

<div class="e404">
  <div class="huge">404</div>
  <div class="big">Page not found.
    <!-- link to the parent folder of _fallback.svelte -->
    <a href={$url('../')}>Go back</a>
  </div>
</div>
