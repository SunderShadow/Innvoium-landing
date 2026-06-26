<script lang="ts" module>
  import type {Snippet} from "svelte"

  export type Props = {
    perPage: number
    children: Snippet
  }
</script>
<script lang="ts">
  import AutoScroller from "$lib/components/AutoScroller.svelte"
  import BezierEasing from "bezier-easing"
  import {onMount} from "svelte"

  let container: HTMLDivElement = $state()!

  function getContainerChildNodes(): HTMLElement[] {
    // @ts-ignore
    return container.childNodes.values().filter(it => it.nodeType == Node.ELEMENT_NODE).toArray()
  }

  let easing = BezierEasing(.22,.59,.76,.99)
  function calcPerspective() {
    for (let el of getContainerChildNodes()) {
      calcElPerspective(el)
    }
  }

  function calcElPerspective(el: HTMLElement) {
    const containerCenter = container.getBoundingClientRect().left + container.getBoundingClientRect().width / 2
    const elCenter = el.getBoundingClientRect().left + el.getBoundingClientRect().width / 2

    const distanceSigned = elCenter / containerCenter - 1
    const distance = Math.abs(distanceSigned)
    const zIndex = Math.max(0, 1 - distance) * 10
    const scale = easing(Math.max(0.6, 1 - distance))



    el.style.setProperty('z-index', zIndex.toFixed())
    el.style.setProperty('transform', `scale(${scale.toString()})`)
  }
  let {
    children
  }: Props = $props()
</script>

<div class="perspective-wrapper">
  <AutoScroller bind:container onscroll={calcPerspective}>
    {@render children?.()}
  </AutoScroller>
</div>

<style lang="scss">
  .perspective-wrapper {
    --auto-scroller-gap: -100px;

    display: contents;

    :global .auto-scroller > * {
      margin-right: var(--auto-scroller-gap);
    }
  }
</style>