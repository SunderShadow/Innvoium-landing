<script lang="ts">
  import avatarEnhanced from "../assets/review-avatar.png?enhanced&format=webp"
  import AutoScroller from "$lib/components/AutoScroller.svelte"
  import Button from "$lib/components/Button.svelte"

  let autoScrollerVelocity = $state(1)
  function handlePrikol(e: MouseEvent) {
    e.preventDefault()
    e.stopPropagation()

    document.body.style.setProperty('cursor', 'ew-resize')

    const initX = e.clientX
    const initVelocity = autoScrollerVelocity

    const spanHTML: HTMLElement = e.target!
    spanHTML.style.display = 'inline-block'
    function timingFunc(distance: number) {
      spanHTML.style.transform = `rotate(${-Math.ceil(distance / 100) * 5}deg)`
      return initVelocity + Math.ceil(distance / 100) * 3
    }

    function move(e: MouseEvent) {
      const moveDistance = e.clientX - initX
      autoScrollerVelocity = timingFunc(moveDistance)
    }

    function end(e: MouseEvent) {
      autoScrollerVelocity = initVelocity
      spanHTML.style.transition = 'transform 500ms cubic-bezier(0.42, 0, 0.11, 2.5)'
      spanHTML.style.removeProperty('transform')

      spanHTML.addEventListener('transitionend', () => {
        spanHTML.style.removeProperty('display')
        spanHTML.style.removeProperty('transition')
      }, {once: true})
      spanHTML.addEventListener('transitioncancel', () => {
        spanHTML.style.removeProperty('display')
        spanHTML.style.removeProperty('transition')
      }, {once: true})

      window.removeEventListener('mousemove', move)
      window.removeEventListener('mouseup', end)
      document.body.style.removeProperty('cursor')
    }

    window.addEventListener('mouseup', end)
    window.addEventListener('mousemove', move)
  }

  function handlePrikolMobile(e: TouchEvent) {
    e.stopPropagation()

    document.body.style.setProperty('overscroll-behavior-x', 'none')
    const initX = e.touches[0].clientX
    const initVelocity = autoScrollerVelocity

    const spanHTML: HTMLElement = e.target!
    spanHTML.style.display = 'inline-block'
    function timingFunc(distance: number) {
      spanHTML.style.transform = `rotate(${-Math.ceil(distance / 100) * 5}deg)`
      return initVelocity + Math.ceil(distance / 100) * 3
    }

    function move(e: TouchEvent) {
      const moveDistance = e.touches[0].clientX - initX
      autoScrollerVelocity = timingFunc(moveDistance)
    }

    function end(e: TouchEvent) {
      autoScrollerVelocity = initVelocity
      spanHTML.style.transition = 'transform 500ms cubic-bezier(0.42, 0, 0.11, 2.5)'
      spanHTML.style.removeProperty('transform')

      document.body.style.removeProperty('overscroll-behavior-x')

      spanHTML.addEventListener('transitionend', () => {
        spanHTML.style.removeProperty('display')
        spanHTML.style.removeProperty('transition')
      }, {once: true})
      spanHTML.addEventListener('transitioncancel', () => {
        spanHTML.style.removeProperty('display')
        spanHTML.style.removeProperty('transition')
      }, {once: true})

      window.removeEventListener('touchmove', move)
      window.removeEventListener('touchend', end)
      document.body.style.removeProperty('cursor')
    }

    window.addEventListener('touchmove', move)
    window.addEventListener('touchend', end)
  }
</script>

{#snippet comment()}
  <article>
    <div class="header">
      <img src={avatarEnhanced.img.src} alt="">
      <div class="name-project">
        <h3>Елизавета Красинская</h3>
        <div>Разработка лендинга</div>
      </div>
      <div class="stars">
        {#each Array(5) as _}
          <svg width="19" height="18" viewBox="0 0 19 18" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M8.38488 0.692677C8.68423 -0.228634 9.98764 -0.228635 10.287 0.692676L11.8056 5.36644C11.9395 5.77846 12.3234 6.05742 12.7566 6.05742H17.6709C18.6397 6.05742 19.0424 7.29704 18.2587 7.86644L14.283 10.755C13.9325 11.0096 13.7858 11.461 13.9197 11.873L15.4383 16.5468C15.7377 17.4681 14.6832 18.2342 13.8995 17.6648L9.92372 14.7763C9.57324 14.5216 9.09864 14.5216 8.74815 14.7763L4.77241 17.6648C3.9887 18.2342 2.93422 17.4681 3.23357 16.5468L4.75217 11.873C4.88604 11.461 4.73938 11.0096 4.3889 10.755L0.413159 7.86644C-0.370555 7.29704 0.0322201 6.05742 1.00094 6.05742H5.91523C6.34845 6.05742 6.73241 5.77846 6.86628 5.36644L8.38488 0.692677Z" fill="#FF7F22"/>
          </svg>
        {/each}
      </div>
    </div>

    <p>I’ve used other kits, but this one is the best. The attention to detail and usability are truly amazing for all designers. I highly recommend it for any type of project.</p>
  </article>
{/snippet}
<section class="page-container">
  <h2>Отзывы кли<span onmousedown={handlePrikol} ontouchstart={handlePrikolMobile}>е</span>нтов и партнеровнтов</h2>

  <div class="content">
    <AutoScroller velocity={autoScrollerVelocity}>
      {@render comment()}
      {@render comment()}
      {@render comment()}
      {@render comment()}
    </AutoScroller>
    <AutoScroller velocity={-autoScrollerVelocity}>
      {@render comment()}
      {@render comment()}
      {@render comment()}
      {@render comment()}
    </AutoScroller>
  </div>

  <div class="show-all">
    <Button outline href="#">Посмотреть все отзывы</Button>
  </div>
</section>

<style lang="scss">
  @use "$lib/scss/mixins/scr";

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  // Prikol
  h2 > span  {
    overscroll-behavior-x: none ;
  }
  section > .content {
    display: flex;
    flex-direction: column;
    gap: 30px;

    > :first-child {
      margin-bottom: 30px;
    }
  }

  article {
    padding: 30px;
    width: 610px;
    flex-shrink: 0;

    background-color: var(--block-bg-color);
    border-radius: 30px;

    @include scr.tablet-and-lower {
      padding: 20px;
    }
    .header {
      display: flex;
      align-items: center;
      gap: 16px;

      margin-bottom: 20px;

      img {
        width: 56px;
        height: 56px;
        border-radius: 10rem;
      }

      .name-project {
        h3 {
          font-size: 20px;
          font-family: Manrope;
          margin: 0;
        }
      }

      .stars {
        margin-left: auto;
        display: flex;
        gap: 2px;
      }
    }
  }

  .show-all {
    display: flex;
    justify-content: center;

    --btn-max-width: 415px;
    --btn-width: 100%;

    margin-left: auto;
    margin-right: auto;
    margin-top: 60px;

    @include scr.tablet-and-lower {
      margin-top: 40px;
    }
  }
</style>