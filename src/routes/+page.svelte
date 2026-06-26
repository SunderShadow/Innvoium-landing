<script lang="ts">
  import HeaderSection from "./+page/sections/HeaderSection.svelte"
  import PartnersSection from "./+page/sections/PartnersSection.svelte"
  import YourInterestSection from "./+page/sections/YourInterestSection.svelte"
  import ServicesSection from "./+page/sections/ServicesSection.svelte"
  import WorkProcessSection from "./+page/sections/WorkProcessSection.svelte"
  import CasesSection from "./+page/sections/CasesSection.svelte"
  import TeamSection from "./+page/sections/TeamSection.svelte"
  import ReviewsSection from "./+page/sections/ReviewsSection.svelte"
  import FAQSection from "./+page/sections/FAQSection.svelte"
  import ContactUsSection from "./+page/sections/ContactUsSection.svelte"
</script>

<svelte:head>
  <title>Инновиум</title>
</svelte:head>

<main>
  <HeaderSection />
  <YourInterestSection />
  <ServicesSection />
  <WorkProcessSection />
  <CasesSection />
<!--  <PartnersSection />-->
  <TeamSection />
<!--  <ReviewsSection />-->
<!--  <FAQSection />-->
<!--  <div class="bottom-figure-section">-->
<!--    <div class="bottom-figure-wrapper">-->
<!--      <svg class="bottom-page-figure" width="1440" height="1272" viewBox="0 0 1440 1272" fill="none" xmlns="http://www.w3.org/2000/svg">-->
<!--        <path d="M404.438 418.476L0 275.531V1272H1440V0L404.438 418.476Z" fill="#811FF1"/>-->
<!--      </svg>-->
<!--    </div>-->

<!--    <div>-->
<!--      <ContactUsSection />-->
<!--    </div>-->
<!--  </div>-->
</main>

<style lang="scss">
  @use "$lib/scss/env";
  @use "$lib/scss/mixins/scr";

  main {
    --section-padding-y: 60px;

    @include scr.tablet-and-lower {
      --section-padding-y: 40px;

      :global section > h2:first-child {
        margin-bottom: 40px;
      }
    }
  }

  .bottom-figure-section {
    position: relative;

    > :last-child {
      position: relative;
      z-index: 2;
    }

    @include scr.tablet-and-lower {
      background: linear-gradient(rgba(env.$primary-color, 0) 20px, rgba(env.$primary-color, .2) 50px, rgba(env.$primary-color, .2) 90%, var(--primary-color));
    }
  }

  .bottom-figure-wrapper {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    max-height: 1200px;
    overflow: hidden;
  }

  .bottom-page-figure {
    width: 100%;
    height: auto;

    @include scr.tablet-and-lower {
      display: none;
    }
  }
</style>