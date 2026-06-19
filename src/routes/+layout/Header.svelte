<script lang="ts">
  import LogoIcon from "$lib/icons/Logo.svelte"
  import Button from "$lib/components/Button.svelte"
</script>

<header>
  <div class="page-container">
    <LogoIcon />
    <nav>
      <a href="#services">Услуги</a>
      <a href="#cases">Кейсы</a>
      <a href="#team">Команда</a>
      <a href="#FAQ">FAQ</a>
    </nav>

    <div class="contact-data">
      <a href="tel:+79996976896">+7 (999) 697-68-96</a>
      <Button>Обсудить проект</Button>
    </div>
  </div>
</header>

<style lang="scss">
  header {
    position: sticky;
    top: 0;
    left: 0;
    z-index: 50;
    width: 100%;
    background: var(--bg-color);
  }

  header > div {
    height: var(--header-height);

    display: flex;
    justify-content: space-between;
    gap: 30px;
    padding: 20px;

    align-items: center;
    border-bottom: 1px solid #F5F7FA;
  }

  nav {
    display: flex;
    gap: 20px;
  }

  .contact-data {
    display: flex;
    gap: inherit;
    align-items: center;

    --btn-font-size: 14px;
    --btn-width: 198px;
    --btn-padding-y: 8px;
    --btn-padding-x: 16px;
  }
</style>