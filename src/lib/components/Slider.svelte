<script lang="ts" module>
  import {type Options} from "@splidejs/svelte-splide"
  import type {Snippet} from "svelte"

  export {SplideSlide as Slide} from "@splidejs/svelte-splide"
  type Props = {
    children: Snippet
    options?: Options
  }
</script>
<script lang="ts">
  import {Splide} from "@splidejs/svelte-splide"

  let {
    children,
    ...props
  }: Props = $props()
</script>

<div class="slider">
  <Splide {...props}>
    {@render children()}
  </Splide>
</div>

<style lang="scss">
  @use "$lib/scss/env";
  @use "$lib/scss/mixins/scr";
  .slider :global {
    .splide__pagination {
      gap: 10px;
      margin-top: 20px;
      margin-left: 0;
      padding-left: 0;
    }

    .splide__arrows {
      position: absolute;
      top: 50%;
      left: 0;
      width: 100%;
      display: flex;
      justify-content: space-between;
      transform: translateY(-50%);
      z-index: 2;

      .splide__arrow {
        background-color: #FFF;
        border-radius: 10rem;
        width: 60px;
        height: 60px;
        border: none;
        cursor: pointer;

        svg {
          width: 15px;

          transition: fill var(--transition-duration);
        }

        transition: background-color var(--transition-duration);

        &:hover {
          background-color: rgba(env.$primary-color, .5);

          svg {
            fill: #FFF;
          }
        }
        &:active {
          background-color: rgba(env.$primary-color, .75);
        }
      }
      .splide__arrow--prev {
        transform: translateX(-50%) rotate(180deg);
      }

      .splide__arrow--next {
        transform: translateX(50%);
      }
    }
    .splide__pagination__page {
      width: 20px;
      height: 20px;
      background-color: #dee0e7;
      border-radius: 100%;
      border: none;

      cursor: pointer;

      display: block;
      transition-duration: var(--transition-duration);
      transition-property: outline, background-color;
      outline: 2px solid transparent;

      @include scr.tablet-and-lower {
        width: 12px;
        height: 12px;

        &.is-active {
          outline-color: var(--primary-color);
        }
      }
      &:hover {
        background-color: var(--primary-color);
      }

      &.is-active {
        background-color: var(--primary-color);
      }
    }
  }
</style>