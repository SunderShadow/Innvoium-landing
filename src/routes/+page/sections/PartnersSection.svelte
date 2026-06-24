<script lang="ts">
  import NightLabsLogo from "$lib/icons/Partners/NightLabs.svelte"
  import VenteilGroupLogo from "$lib/icons/Partners/VenteilGroup.svelte"
  import Boosty2BLogo from "$lib/icons/Partners/Boosty2B.svelte"
  import PrintfulLogo from "$lib/icons/Partners/Printful.svelte"
  import RemoteLogo from "$lib/icons/Partners/Remote.svelte"
  import ClutchLogo from "$lib/icons/Partners/Clutch.svelte"
  import AutoScroller from "$lib/components/AutoScroller.svelte"
</script>

<section id="partners" class="page-container">
  <h2>Партнеры</h2>
  <AutoScroller>
    <a href="https://vgarda.com/"><VenteilGroupLogo /></a>
    <a href=""><NightLabsLogo /></a>
    <a href=""><Boosty2BLogo /></a>
    <a href=""><PrintfulLogo /></a>
    <a href=""><RemoteLogo /></a>
    <a href=""><ClutchLogo /></a>
  </AutoScroller>
</section>

<style lang="scss">
  h2 {
    margin: 0 0 60px;
  }

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  a {
    display: flex;
    align-items: center;
    :global svg {
      max-width: 80px;
      height: auto;
    }
  }
</style>