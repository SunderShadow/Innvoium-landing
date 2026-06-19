<script lang="ts" module>
  import type {Snippet} from "svelte"

  export type Props = {
    rtl?: boolean
    children: Snippet
  }
</script>
<script lang="ts">
  import {onMount} from "svelte"

  let container: HTMLElement = $state()!

  const gap = 30 //px

  // Инициализируется в onMount
  let itemWidth: number = 0 //px
  // Инициализируется в onMount
  let scrollOffset = 0 // px
  let scrollRtlOffset = 0 // px

  let currentScroll = 0
  const scrollPerSec = 1 //px

  let autoScroll = false

  function startAutoScroll() {
    if (autoScroll) return

    autoScroll = true
    scrollMembers()
  }

  let {
    rtl = false,
    children
  }: Props = $props()

  function infiniteScroll() {
    if (container.scrollLeft <= scrollOffset) {
      const destination = scrollOffset - container.scrollLeft
      const lastItem = container.lastElementChild!
      const cloneLastItem = lastItem.cloneNode(true)
      container.prepend(cloneLastItem)
      lastItem.remove()

      requestAnimationFrame(() => {
        container.scrollTo({left: scrollOffset * 2 - destination})
      })
    }

    if (container.scrollLeft >= scrollOffset * 3) {
      const destination = container.scrollLeft - scrollOffset * 3
      const firstItem = container.querySelector(':first-child')!
      const cloneFirstItem = firstItem.cloneNode(true)
      container.append(cloneFirstItem)
      firstItem.remove()

      requestAnimationFrame(() => {
        container.scrollTo({left: scrollOffset * 2 + destination})
      })
    }
  }

  function stopAutoScroll() {
    autoScroll = false
  }

  function scrollMembers() {
    if (!autoScroll) return

    if (rtl) {
      currentScroll = container.scrollLeft - scrollPerSec
    } else {
      currentScroll = container.scrollLeft + scrollPerSec
    }
    container.scrollTo({left: currentScroll})
    requestAnimationFrame(scrollMembers)
  }

  onMount(() => {
    itemWidth = container.querySelector(':first-child')!.offsetWidth
    scrollOffset = itemWidth + gap

    if (rtl) {
      container.scrollTo({left: scrollOffset * 2})
      currentScroll = container.scrollLeft
    }

    const itemsToAdd = Math.max(0, Math.ceil(container.offsetWidth / itemWidth) + 4 - container.childElementCount)
    // @ts-ignore
    const childElements = container.childNodes.values().filter(it => it.nodeType !== Node.COMMENT_NODE).toArray()
    for (let i = 0; i < itemsToAdd; i++) {
      container.append(childElements[i].cloneNode(true))
    }

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
    &::-webkit-scrollbar {
      display: none;
    }
  }
</style>