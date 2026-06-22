<script lang="ts">
  import NightLabsLogo from "$lib/icons/Partners/NightLabs.svelte"
  import VenteilGroupLogo from "$lib/icons/Partners/VenteilGroup.svelte"
  import Boosty2BLogo from "$lib/icons/Partners/Boosty2B.svelte"
</script>

<section id="partners" class="page-container">
  <h2>Партнеры</h2>
  <div class="partners">
    <a href="https://vgarda.com/"><VenteilGroupLogo /></a>
    <a href=""><NightLabsLogo /></a>
    <a href=""><Boosty2BLogo /></a>
  </div>
</section>

<style lang="scss">
  h2 {
    margin: 0 0 60px;
  }

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  .partners {
    display: flex;
    align-items: center;
    gap: 60px;
  }
</style>