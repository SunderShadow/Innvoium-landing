<script lang="ts">
  import bgImgDesktop from "../assets/header-section-bg.png?enhanced&format=webp"
  import Button from "$lib/components/Button.svelte"
</script>

<svelte:head>
  <link rel="preload" as="image" href={bgImgDesktop.img.src} fetchpriority="high">
</svelte:head>

<section class="page-container" id="header-section" style:--bg-img-desktop="url('{bgImgDesktop.img.src}')">
  <h1>
    Автоматизируем рутину вашего бизнеса за 30 дней<br>
    <span>от анализа до запуска под ключ</span>
  </h1>

  <p>Нейроворонки, чат-боты, CRM, интеграция ИИ<br>и другие цифровые сервисы</p>
  <Button href="#contact-us">Получить консультацию</Button>
</section>

<style lang="scss">
  section {
    background-image: var(--bg-img-desktop);
    background-size: cover;
    padding-top: 100px;
    padding-top: 100px;

    --btn-width: 412px;
  }

  p {
    margin-top: 46px;
    margin-bottom: 46px;
  }

  h1 {
    max-width: 730px;
    margin: 0;

    span {
      color: var(--primary-color);
    }
  }
</style>