<script lang="ts">
  import LogoIcon from "$lib/icons/Logo.svelte"
  import Button from "$lib/components/Button.svelte"
  import {onMount} from "svelte"

  let windowIsMobile = $state(false)
  onMount(() => {
    window.addEventListener('resize', () => {
      windowIsMobile = window.screen.width <= 1024
    })
    windowIsMobile = window.screen.width <= 1024
  })

  let menu: HTMLElement = $state()!
  function removeMenuIfClosed(e: TransitionEvent) {
    if (e.propertyName == 'background-color') {
      if (!mobileMenuOpened) {
        e.currentTarget.style.setProperty('display', 'none')
      }
    }
  }

  function toggleMenu() {
    if (!mobileMenuOpened) {
      menu.style.removeProperty('display')
      requestAnimationFrame(() => {
        mobileMenuOpened = !mobileMenuOpened
      })
    } else {
      mobileMenuOpened = !mobileMenuOpened
    }
  }

  function closeMenuIfParentClick(e: Event) {
    if (e.currentTarget == e.target) {
      toggleMenu()
    }
  }
  let mobileMenuOpened = $state(false)
</script>

<header>
  <div class="page-container">
    <div class="logo">
      <LogoIcon />
    </div>

    <button id="mobile-menu-btn" class:active={mobileMenuOpened} onclick={toggleMenu}>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
    </button>

    <div bind:this={menu} class="mobile-menu" onclick={closeMenuIfParentClick} class:open={mobileMenuOpened} ontransitionend={removeMenuIfClosed}>
    <!--   Внешний контейнер создает тень, внутренний - окошко для контента-->
      <div>
        <nav>
          <a href="#services">Услуги</a>
          <a href="#cases">Кейсы</a>
          <a href="#team">Команда</a>
          <a href="#FAQ">FAQ</a>
        </nav>

        <div class="contact-data">
          <a href="tel:+79996976896">+7 (999) 697-68-96</a>
          <Button outline={windowIsMobile}>Обсудить проект</Button>
        </div>
      </div>
    </div>
  </div>
</header>

<style lang="scss">
  @use "$lib/scss/mixins/scr";

  header {
    position: sticky;
    top: 0;
    left: 0;
    z-index: 30;
    width: 100%;
    background: var(--bg-color);
  }

  header > div {
    position: relative;
    height: var(--header-height);

    display: flex;
    justify-content: space-between;
    gap: 178px;
    padding: 20px;

    align-items: center;
    border-bottom: 1px solid #F5F7FA;

    @media (max-width: 1200px) {
      gap: 60px;
    }
  }

  .logo {
    flex-shrink: 0;

    @include scr.tablet-and-lower {
      :global svg {
        width: 148px;
        height: auto;
      }
    }
  }

  #mobile-menu-btn {
    border: none;
    background: none;
    outline: none;

    --width: 9px;
    --gap: 4px;

    width: 24px;
    height: 24px;
    position: relative;

    display: none;
    @include scr.tablet-and-lower {
      display: block;
    }

    span {
      display: block;
      background-color: #000;
      position: absolute;
      top: 50%;
      left: 50%;
      width: var(--width);
      height: 2px;
      transform-origin: center;
      transition: transform var(--transition-duration);
    }

    span:nth-child(1) {
      transform: translate(calc(-50% - var(--width) / 2), calc(-50% - var(--gap) / 2));
    }

    span:nth-child(2) {
      transform: translate(calc(-50% + var(--width) / 2), calc(-50% - var(--gap) / 2));
    }

    span:nth-child(3) {
      transform: translate(calc(-50% - var(--width) / 2), calc(-50% + var(--gap) / 2));
    }

    span:nth-child(4) {
      transform: translate(calc(-50% + var(--width) / 2), calc(-50% + var(--gap) / 2));
    }

    &.active {
      span:nth-child(1) {
        transform: translate(calc(-50% - var(--width) / 2 + 1px), calc(-50% - var(--gap) / 2)) rotate(25deg);
      }

      span:nth-child(2) {
        transform: translate(calc(-50% + var(--width) / 2 - 1px), calc(-50% - var(--gap) / 2)) rotate(-25deg);
      }

      span:nth-child(3) {
        transform: translate(calc(-50% - var(--width) / 2 + 1px), calc(-50% + var(--gap) / 2)) rotate(-25deg);
      }

      span:nth-child(4) {
        transform: translate(calc(-50% + var(--width) / 2 - 1px), calc(-50% + var(--gap) / 2)) rotate(25deg);
      }

    }
  }

  nav {
    display: flex;
    gap: 20px;
  }

  .contact-data {
    display: flex;
    gap: inherit;
    align-items: center;

    a {
      font-weight: 700;
    }

    font-size: 14px;
    --btn-font-size: 14px;
    --btn-width: 198px;
    --btn-padding-y: 8px;
    --btn-padding-x: 16px;

    @include scr.tablet-and-lower {
      --btn-width: 150px;
      --btn-font-size: 12px;

      flex-direction: column;
      align-items: center;
      gap: 15px;
    }
  }

  .mobile-menu {
    @include scr.tablet-and-lower {
      position: fixed;
      left: 0;
      top: var(--header-height);
      right: 0;
      bottom: 0;

      z-index: 20;

      background: transparent;
      transition-property: background-color;
      transition-duration: var(--transition-duration);
      transition-delay: 0, var(--transition-duration);

      &.open {
        background: rgba(#000, .1);
      }

      &:not(.open) {
        > div {
          transform: translateX(100%);
        }
      }
    }

    > div {
      position: absolute;
      right: 0;
      top: 0;
      background: var(--bg-color);
      border-bottom-left-radius: 30px;
      padding: 30px;
      display: flex;

      justify-content: space-between;
      align-items: center;
      gap: 30px;

      transition-property: transform;
        transition-duration: var(--transition-duration);
      width: 100%;

      @include scr.tablet-and-lower {
        flex-direction: column;
        gap: 60px;

        width: 210px;

        nav {
          flex-direction: column;
          align-items: center;
        }
      }
    }
  }
</style>