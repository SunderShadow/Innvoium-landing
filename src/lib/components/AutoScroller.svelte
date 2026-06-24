<script lang="ts" module>
  import type {Snippet} from "svelte"

  export type Props = {
    velocity?: number
    children: Snippet
  }
</script>
<script lang="ts">
  import {onMount} from "svelte"

  let {
    velocity = 1,
    children
  }: Props = $props()

  let container: HTMLElement = $state()!

  let gap = 30 //px

  let autoScrollRun = false

  function infiniteScroll() {
    if (container.getBoundingClientRect().left < nextLeftEl.getBoundingClientRect().right + gap) {
      const lastChild = getContainerChildNodes()[getContainerChildNodes().length - 1]

      calcSkipDistance()
      calcNextElementsWidth()

      let scrollWidth = container.scrollLeft + lastChild.offsetWidth + gap

      container.prepend(lastChild.cloneNode(true))
      lastChild.remove()

      container.scrollTo({left: scrollWidth})
    } else if (container.getBoundingClientRect().right > nextRightEl.getBoundingClientRect().right + gap) {
      const firstChild = getContainerChildNodes()[0]

      calcSkipDistance()
      calcNextElementsWidth()

      let scrollWidth = container.scrollLeft - firstChild.offsetWidth - gap

      container.append(firstChild.cloneNode(true))
      firstChild.remove()

      container.scrollTo({left: scrollWidth})
    }
  }

  function calcAutoScroll() {
    if (!autoScrollRun) return

    container.scrollTo({left: container.scrollLeft - velocity})

    requestAnimationFrame(calcAutoScroll)
  }

  function startAutoScroll() {
    autoScrollRun = true
    requestAnimationFrame(calcAutoScroll)
  }

  function stopAutoScroll() {
    autoScrollRun = false
  }

  function getContainerChildNodes(): HTMLElement[] {
    // @ts-ignore
    return container.childNodes.values().filter(it => it.nodeType == Node.ELEMENT_NODE).toArray()
  }

  const skipElementsCount = 2
  let skippedDistance = 0
  function calcSkipDistance() {
    skippedDistance = 0
    for (let i = 0; i < skipElementsCount; i++) {
      skippedDistance += getContainerChildNodes()[i].offsetWidth + gap
    }
  }

  let nextLeftEl: HTMLElement
  let nextRightEl: HTMLElement
  function calcNextElementsWidth() {
    const childNodes = getContainerChildNodes()
    nextLeftEl = childNodes[skipElementsCount - 1]

    let accumulatedWidth = 0
    for (let i = skipElementsCount; i < childNodes.length; i++) {
      accumulatedWidth += childNodes[i].offsetWidth

      if (container.offsetWidth <= accumulatedWidth) {
        nextRightEl = childNodes[i - skipElementsCount + 1]
        return
      }
    }
  }

  onMount(() => {
    gap = Number(getComputedStyle(container).gap.slice(0, -2))

    let childNodes = getContainerChildNodes()
    for (let i = 0; i < childNodes.length; i++) {
      container.append(childNodes[i].cloneNode(true))
    }

    childNodes = getContainerChildNodes()
    calcSkipDistance()
    calcNextElementsWidth()
    container.scrollTo({left: skippedDistance})

    startAutoScroll()
  })
</script>

<div
    role="contentinfo"
    class="auto-scroller"
    bind:this={container}
    ontouchstart={stopAutoScroll}
    ontouchend={startAutoScroll}
    onscroll={infiniteScroll}
    onmouseenter={stopAutoScroll}
    onmouseleave={startAutoScroll}
>
  {@render children()}
</div>

<style lang="scss">

  .auto-scroller {
    display: flex;

    gap: 30px;
    width: 100%;
    overflow: scroll;
    scrollbar-width: none;

    :global > * {
      flex-shrink: 0;
    }
    &::-webkit-scrollbar {
      display: none;
    }
  }
</style>