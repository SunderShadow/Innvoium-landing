<script lang="ts">
  import caseThumb from "../assets/case-thumb.png?enhanced&format=webp"
  import CaseComponent, {type Case} from "$lib/components/CaseComponent.svelte"
  import {onMount} from "svelte"
  import {browser} from "$app/env"
  import * as Slider from "$lib/components/Slider.svelte"
  import type {Options} from "@splidejs/svelte-splide"

  let cases: Case[] = [
    {
      id: 1,
      imgSrc: caseThumb.img.src,
      title: 'Разработка инновационного продукта по измерению уровня зумерства',
      description: 'Роскосмос обратился с проблемой ежедневного залипания зумеров в телефоны, убивая процент продаж и полезного действия. Для улучшения качества работы мы создали ультра модный провод',
      meta: {
        duration: '12 дней',
        cost: 3000000
      }
    },
    {
      id: 2,
      imgSrc: caseThumb.img.src,
      title: 'Разработка инновационного new Product',
      description: 'Роскосмос обратился с проблемой ежедневного залипания зумеров в телефоны, убивая процент продаж и полезного действия. Для улучшения качества работы мы создали ультра модный провод',
      meta: {
        duration: '12 дней',
        cost: 300000
      }
    },
    {
      id: 3,
      imgSrc: caseThumb.img.src,
      title: 'Разработка инновационного продукта по измерению уровня зумерства',
      description: 'Роскосмос обратился с проблемой ежедневного залипания зумеров в телефоны, убивая процент продаж и полезного действия. Для улучшения качества работы мы создали ультра модный провод',
      meta: {
        duration: '12 дней',
        cost: 300000
      }
    },
    {
      id: 4,
      imgSrc: caseThumb.img.src,
      title: 'Разработка инновационного продукта по измерению уровня зумерства',
      description: 'Роскосмос обратился с проблемой ежедневного залипания зумеров в телефоны, убивая процент продаж и полезного действия. Для улучшения качества работы мы создали ультра модный провод',
      meta: {
        duration: '12 дней',
        cost: 300000
      }
    }
  ]

  let selectedCase: Case = $state(cases[0])

  let focusContainer: HTMLElement = $state()!
  function selectCase(_case: Case) {
    selectedCase = _case
  }

  function setCaseFocused(i: number) {
    if (newFocusComponentI == i || newFocusComponentI !== lastFocusComponentContainer) return

    newFocusComponentI = i
    caseShrink[i] = true
    const caseContainer: HTMLElement = caseContainers[i]
    const _case: HTMLElement = caseContainer.lastElementChild!
    const originRect = _case.getBoundingClientRect()
    const focusContainerRect = focusContainer.getBoundingClientRect()
    const topAbsolute = document.body.getBoundingClientRect().top * -1 + originRect.top
    const leftAbsolute = originRect.left

    _case.style.setProperty('position', 'absolute')
    _case.style.setProperty('left', leftAbsolute + 'px')
    _case.style.setProperty('top', topAbsolute + 'px')
    _case.style.setProperty('width', originRect.width + 'px')
    _case.style.setProperty('height', originRect.height + 'px')
    _case.style.setProperty('transition-property', 'width, height, left, top')
    _case.style.setProperty('transition-duration', '  400ms')

    requestAnimationFrame(() => {
      _case.style.setProperty('left', focusContainerRect.left + 'px')
      _case.style.setProperty('top', document.body.getBoundingClientRect().top * -1 + focusContainerRect.top + 'px')
      _case.ontransitionend = (e: TransitionEvent) => {
        if (e.propertyName == 'left') {
          _case.style.setProperty('width', focusContainerRect.width + 'px')
          _case.style.setProperty('height', focusContainerRect.height + 'px')

          _case.ontransitionend = (e) => {
            if (e.propertyName == 'width') {
              _case.style.removeProperty('position')
              _case.style.removeProperty('left')
              _case.style.removeProperty('top')
              _case.style.removeProperty('width')
              _case.style.removeProperty('transition-property')
              _case.style.removeProperty('transition-duration')

              if (focusContainer.childElementCount == 1) {
                focusContainer.firstElementChild.style.removeProperty('height')
                caseFull[lastFocusComponentContainer] = false
                caseContainers[lastFocusComponentContainer].append(focusContainer.firstElementChild)
              }

              focusContainer.append(_case)
              caseFull[i] = true
              caseShrink[i] = false
              lastFocusComponentContainer = newFocusComponentI
            }
          }
        }
      }
    })
  }

  let lastFocusComponentContainer = $state(-1)
  let newFocusComponentI: number = $state(-1)
  let caseContainers: HTMLDivElement[] = $state(Array(cases.length).fill(null))
  let caseFull = $state(Array(cases.length).fill(false))
  let caseShrink = $state(Array(cases.length).fill(false))

  const sliderOptions: Options = {
    type: 'loop',
    autoplay: true,
    interval: 3000,
    perPage: 1,
    arrows: false,
    gap: 10
  }

  let mobile = $state(false)
  onMount(() => {
    if (browser) {
      mobile = window.screen.width < 1024
      window.addEventListener('resize', () => {
        mobile = window.screen.width < 1024

        if (!mobile) {
          requestAnimationFrame(() => {setCaseFocused(0)})
        }
      })
    }

    if (!mobile) {
      requestAnimationFrame(() => {setCaseFocused(0)})
    }
  })
</script>

{#snippet caseItem(_case)}
  <article class="case" class:focused={_case.id == selectedCase.id} onclick={() => {selectCase(_case)}} >
    <img src={_case.imgSrc} alt="" loading="lazy">
    <div class="content">
      <h3>{_case.title}</h3>
    </div>
  </article>
{/snippet}

<section id="cases" class="page-container">
  <div class="header">
    <h2>Кейсы</h2>
    <a class="active" href="/">все кейсы →</a>
  </div>

  {#if mobile}
    <Slider.default options={sliderOptions}>
      {#each cases as data}
        <Slider.Slide>
          <CaseComponent {data} full/>
        </Slider.Slide>
      {/each}
    </Slider.default>
  {:else}
    <div class="content">
      <div bind:this={focusContainer}>
      </div>
      <div class="case-selection">
        {#each cases as data, i (i)}
          <div onclick={e => {setCaseFocused(i)}} bind:this={caseContainers[i]}>
            <CaseComponent {data} full={caseFull[i]} shrink={caseShrink[i]}/>
            {#if lastFocusComponentContainer == i || newFocusComponentI == i}
              <CaseComponent active={newFocusComponentI == i} {data} />
            {/if}
          </div>
        {/each}
      </div>
    </div>

  {/if}
</section>

<style lang="scss">
  @use "$lib/scss/mixins/scr";

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    margin-bottom: 60px;

    a {
      font-weight: 700;
    }
  }

  section > .content {
    display: flex;
    gap: 30px;

    > *:first-child {
      flex-shrink: 0;
      max-width: 605px;
      width: 100%;
    }

    @include scr.tablet-and-lower {
      flex-direction: column;
    }
  }

  h2 {
    margin: 0;
  }

  .case-selection {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 20px;
  }
</style>