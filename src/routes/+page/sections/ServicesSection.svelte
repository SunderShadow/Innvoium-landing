<script lang="ts">
  // or only core styles
  import '@splidejs/svelte-splide/css/core';
  import {type Options} from "@splidejs/svelte-splide"
  import Button from "$lib/components/Button.svelte"
  import * as Slider from "$lib/components/Slider.svelte"

  const splideOptions: Options = {
    type: 'loop',
    autoplay: true,
    interval: 3000,
    perPage: 3,
    gap: 30,
    breakpoints: {
      1024: {
        perPage: 2,
      },
      700: {
        arrows: false
      },
      550: {
        perPage: 1,
      }
    }
  }
</script>

{#snippet itemCard(title, textContent, cost, href, hit = false)}
  <article class:hit>
    <h3>{title}</h3>
    <p>{textContent}</p>
    <data value={cost} class="cost">от {cost} ₽/час</data>
    <a class="active" href={href}>подробнее →</a>
  </article>
{/snippet}

<section id="services" class="page-container">
  <h2>Услуги</h2>

  <div class="content">
    <Slider.default options={splideOptions}>
      <Slider.Slide>
        {@render itemCard('Нейроворонки', 'Строим автоматизированные воронки продаж на базе ИИ', 3000, '#', true)}
      </Slider.Slide>
      <Slider.Slide>
        {@render itemCard('ИИ-интеграции', 'Внедрение ИИ в бизнес-процессы: умные чат-боты и ассистенты', 3000, '#')}
      </Slider.Slide>
      <Slider.Slide>
        {@render itemCard('CRM и другие системы', 'Настройка, интеграция и создание систем:  воронки продаж, напоминания и другое', 3000, '#')}
      </Slider.Slide>
      <Slider.Slide>
        {@render itemCard('Нейроворонки', 'Строим автоматизированные воронки продаж на базе ИИ', 3000, '#', true)}
      </Slider.Slide>
      <Slider.Slide>
        {@render itemCard('ИИ-интеграции', 'Внедрение ИИ в бизнес-процессы: умные чат-боты и ассистенты', 3000, '#')}
      </Slider.Slide>
      <Slider.Slide>
        {@render itemCard('CRM и другие системы', 'Настройка, интеграция и создание систем:  воронки продаж, напоминания и другое', 3000, '#')}
      </Slider.Slide>
    </Slider.default>
  </div>

  <div class="btn">
    <Button>Не нашли свою задачу? Обсудим индивидуально</Button>
  </div>
</section>

<style lang="scss">
  @use "$lib/scss/mixins/scr";
  @use "$lib/scss/env";

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  #services .btn {
    --btn-max-width: 638px;
    --btn-width: 100%;

    display: flex;
    justify-content: center;

    margin-top: 60px;
    margin-left: auto;
    margin-right: auto;
  }


  article {
    position: relative;
    background-color: #F5F7FA;
    padding: 30px;
    border-radius: 30px;

    &.hit {
      background-color: rgba(env.$primary-color, .15);
    }

    h3 {
      margin: 0;
      font-size: 1.5em;
    }

    p {
      margin: 20px 0;
      line-height: 1.7;
    }

    .cost {
      display: block;
      font-size: 1.5em;
      font-weight: 600;
      margin-bottom: 30px;
    }

    a {
      font-weight: 600;

      &::before {
        content: '';
        position: absolute;
        top: 0; left: 0; bottom: 0; right: 0;
      }
    }
  }
</style>