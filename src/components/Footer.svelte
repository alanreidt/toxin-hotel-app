<script>
  import FooterTitres from "./FooterTitres.svelte";
  import FooterInfo from "./FooterInfo.svelte";
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .footer {
    .block-default-styles();

    background-color: #fff;
  }
</style>

<footer class="footer">
  <div class="footer__footer-info">
    <FooterInfo />
  </div>
  <div class="footer__footer-titres">
    <FooterTitres />
  </div>
</footer>
