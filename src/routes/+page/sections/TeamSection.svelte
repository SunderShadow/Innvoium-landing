<script lang="ts">
  import alexandrShvedovEnhanced from "../assets/team-section/alexandr-shvedov.png?enhanced&format=webp"
  import valeriySidorovEnhanced from "../assets/team-section/valeriy-sidorov.png?enhanced&format=webp"
  import maksimTepinEnhanced from "../assets/team-section/maksim-tepin.png?enhanced&format=webp"
  import alisaLarinaEnhanced from "../assets/team-section/alisa-larina.png?enhanced&format=webp"
  import georgiySherbinEnhanced from "../assets/team-section/georgiy-sherbin.png?enhanced&format=webp"
  import {onMount, tick} from "svelte"
  import AutoScroller from "$lib/components/AutoScroller.svelte"

  let members: Member[] = $state([
    {
      img: alexandrShvedovEnhanced.img.src,
      name: 'Александр Шведов',
      position: 'разработчик'
    },
    {
      img: valeriySidorovEnhanced.img.src,
      name: 'Валерий Сидоров',
      position: 'маркетолог'
    },
    {
      img: maksimTepinEnhanced.img.src,
      name: 'Максим Тепин',
      position: 'основатель Инновиума'
    },
    {
      img: alisaLarinaEnhanced.img.src,
      name: 'Алиса Ларина',
      position: 'дизайнер'
    },
    {
      img: georgiySherbinEnhanced.img.src,
      name: 'Георгий Щербинин',
      position: 'проектный менеджер, SEO-спец'
    }
  ])

  type Member = {
    img: string,
    name: string,
    position: string
  }
</script>

{#snippet memberCard(imgSrc, name, position)}
  <figure class="member">
    <img src={imgSrc} alt="">
    <figcaption>
      <h3>{name}</h3>
      <p>{position}</p>
    </figcaption>
  </figure>
{/snippet}

<section id="team" class="page-container">
  <div class="header">
    <h2>Команда</h2>
    <div>все проекты делали эти <span>люди</span></div>
  </div>

  <AutoScroller rtl>
    {#each members as member, i (i)}
      {@render memberCard(member.img, member.name, member.position)}
    {/each}
  </AutoScroller>
</section>

<style lang="scss">
  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    margin-bottom: 60px;

    span {
      color: var(--primary-color);
    }

    div {
      font-weight: 700;
    }
  }

  h2 {
    margin: 0;
  }

  .member {
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    text-align: center;

    color: #FFF;

    margin: 0;

    position: relative;
    aspect-ratio: 400 / 500;
    width: 100%;
    max-width: 400px;
    border-radius: 30px;
    padding: 30px;

    img {
      position: absolute;
      width: 100%;
      height: 100%;
      display: block;
      object-fit: cover;

      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      border-radius: inherit;
      z-index: 2;
    }

    h3 {
      margin: 0;
      font-family: Manrope, sans-serif;
    }

    p {
      margin: 0;
    }

    figcaption {
      position: relative;
      z-index: 3;
    }
  }
</style>