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

<main>
  <HeaderSection />
  <PartnersSection />
  <YourInterestSection />
  <ServicesSection />
  <WorkProcessSection />
  <CasesSection />
  <TeamSection />
  <ReviewsSection />
  <FAQSection />
  <div class="bottom-figure-wrapper">
    <svg class="bottom-page-figure" width="1440" height="1272" viewBox="0 0 1440 1272" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M404.438 418.476L0 275.531V1272H1440V0L404.438 418.476Z" fill="#811FF1"/>
    </svg>

    <div>
      <ContactUsSection />
    </div>
  </div>
</main>

<style lang="scss">
  main {
    --section-padding-y: 60px;
  }

  .bottom-figure-wrapper {
    position: relative;
    > :last-child {
      position: relative;
      z-index: 2;
    }
  }

  .bottom-page-figure {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: auto;
  }
</style>