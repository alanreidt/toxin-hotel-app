<script>
  import Topline from "../components/Topline.svelte";
  import Footer from "../components/Footer.svelte";

  import { page, url } from '@sveltech/routify';

  $: currentPageHref = $url($page.path);
</script>

<style lang="less">
  //- This is a modification of code from https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/site.css

  /**
  * 1. Avoid the IE 10-11 `min-height` bug.
  * 2. Set `flex-shrink` to `0` to prevent some browsers from
  *    letting these items shrink to smaller than their content's default
  *    minimum size. See http://bit.ly/1Mn35US for details.
  * 3. Use `%` instead of `vh` since `vh` is buggy in older mobile Safari.
  */

  .page {
    display: flex;
    flex-direction: column;
    min-height: 100vh;

    /* margin: 0; */
    box-sizing: border-box;

    &__header,
    &__footer {
      flex: none; /* 2 */
    }

    &__content {
      flex: 1 0 auto; /* 2 */
    }
  }
</style>

<div class="page">
  <div class="page__header">
    <Topline options={{currentPageHref}}/>
  </div>

  <main class="page__content">
    <slot />
  </main>

  <div class="page__footer">
    <Footer />
  </div>
</div>
