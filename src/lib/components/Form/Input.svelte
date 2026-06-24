<script lang="ts" module>
  import type {
    Component,
    Snippet,
  } from "svelte"

  import type {HTMLInputAttributes} from "svelte/elements"

  type Props = HTMLInputAttributes & {
    svg: Snippet | Component
    value: any
  }
</script>
<script lang="ts">
  let {
    svg,
    value = $bindable(),
    ...restProps
  }: Props = $props()
</script>

<div class="input">
  <input type="text" {...restProps} bind:value>
  <div class="svg">
    {@render svg?.()}
  </div>
</div>

<style lang="scss">
  @use "$lib/scss/mixins/scr";
  @use "$lib/scss/env";

  .input {
    position: relative;
    width: 100%;

    &:hover {
      :global svg {
        *[fill] {
          fill: rgba(env.$primary-color, .5);
        }
        *[stroke] {
          stroke: rgba(env.$primary-color, .5);
        }
      }

      input {
        border-color: rgba(env.$primary-color, .5);
      }
    }

    &:focus-within {
      :global svg {
        *[fill] {
          fill: var(--primary-color);
        }
        *[stroke] {
          stroke: var(--primary-color);
        }
      }

      input {
        border-color: var(--primary-color);
      }
    }

    :global svg {
      *[fill] {
        transition: fill var(--transition-duration);
      }
      *[stroke] {
        transition: stroke var(--transition-duration);
      }
    }

    input {
      width: 100%;
      border-radius: 10rem;
      padding: 18px 30px;
      border: 1px solid transparent;
      outline: none;
      font: inherit;

      @include scr.tablet-and-lower {
        padding: 12px 20px;
      }

      background-color: var(--input-bg-color, #FFF);

      transition: border var(--transition-duration);
    }

    .svg {
      position: absolute;
      right: 20px;
      top: 50%;
      transform: translateY(-50%);
      height: 1em;

      :global svg {
        display: block;
        height: 100%;
      }
    }
  }
</style>