<script lang="ts" module>
  import type {Snippet} from "svelte"
  import type {HTMLButtonAttributes} from "svelte/elements"

  export type Props = HTMLButtonAttributes & {
    outline?: boolean
    href?: string
    children: Snippet
  }
</script>
<script lang="ts">
  let {
    outline = false,
    href,
    children,
    ...restProps
  }: Props = $props()
</script>

{#if href}
  <a class="button" class:outline {href}>{@render children()}</a>
{:else}
  <button {...restProps} class:outline>
    {@render children()}
  </button>
{/if}


<style lang="scss">
  a, button {
    display: block;
    --color: var(--btn-color, var(--primary-color));

    width: var(--btn-width, fit-content);
    max-width: var(--btn-max-width, auto);

    text-align: center;

    padding: var(--btn-padding-y, 16px) var(--btn-padding-x, 20px);

    border: 2px solid var(--color);

    border-radius: 100rem;
    background: var(--color);
    color: #FFF;

    font: inherit;
    font-weight: 600;
    font-size: var(--btn-font-size, inherit);
    cursor: pointer;

    transition-duration: var(--transition-duration);
    transition-property: background-color, color, background-color;

    &.outline {
      color: var(--color);
      background: transparent;
    }

    &:hover {
      --color: var(--primary-color-darker);
    }
  }
</style>