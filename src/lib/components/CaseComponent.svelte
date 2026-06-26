<script lang="ts" module>
  import {slide} from "svelte/transition"
  export type Case = {
    id: number,
    imgSrc: string,
    title: string,
    description: string
    meta: {
      duration: string,
      cost: number,
    },
  }

  type Props = {
    active?: boolean
    shrink?: boolean
    full?: boolean
    data: Case
  }

  function formatCost(cost: number): string {
    const costStr = cost.toString().split('').reverse()
    let newCostStr = ''

    for (let i = costStr.length - 1; i > 0; i--) {
      newCostStr += costStr[i]
      if ((i ) % 3 == 0) {
        newCostStr += '.'
      }
    }

    newCostStr += costStr[0]
    return newCostStr
  }
</script>
<script lang="ts">
  let {
    active = false,
    shrink = false,
    full = false,
    data
  }: Props = $props()
</script>

<div class="case" class:full class:active>
  <img src={data.imgSrc} alt="">
  {#if full && !shrink}
    <div class="content" in:slide>
      <h3>{data.title}</h3>
      <div class="meta">
        <time datetime="12d 0h 0m 0s" class="time">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10 2H14M12 14V10M4 13C4.24486 11.056 5.19466 9.26941 6.66925 7.97914C8.14384 6.68887 10.0407 5.98464 12 6C13.294 6.00138 14.5684 6.31664 15.7139 6.91876C16.8593 7.52088 17.8416 8.39187 18.5764 9.45702C19.3113 10.5222 19.7768 11.7497 19.933 13.0343C20.0892 14.3189 19.9315 15.6222 19.4733 16.8324C19.0152 18.0426 18.2703 19.1236 17.3025 19.9827C16.3348 20.8418 15.1731 21.4533 13.9171 21.7648C12.6611 22.0763 11.3482 22.0784 10.0912 21.771C8.83422 21.4637 7.67054 20.8559 6.7 20L4 17.6M9 17H4V22" stroke="#1A1D29" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <span>{data.meta.duration}</span>
        </time>
        <data value="300000">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M6 12H6.01M18 12H18.01M4 6H20C21.1046 6 22 6.89543 22 8V16C22 17.1046 21.1046 18 20 18H4C2.89543 18 2 17.1046 2 16V8C2 6.89543 2.89543 6 4 6ZM14 12C14 13.1046 13.1046 14 12 14C10.8954 14 10 13.1046 10 12C10 10.8954 10.8954 10 12 10C13.1046 10 14 10.8954 14 12Z" stroke="#1A1D29" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <span>{formatCost(data.meta.cost)}₽</span>
        </data>
      </div>

      <p>
        {data.description}
      </p>

      <a class="active" href="/">подробнее →</a>
    </div>
  {:else if !full && !shrink}
    <div class="content" out:slide>
      <h3>{data.title}</h3>
    </div>
  {/if}
</div>

<style lang="scss">
  @use "$lib/scss/env";

  .case {
    background-color: var(--block-bg-color);
    border-radius: 30px;

    cursor: pointer;

    transition: background-color var(--transition-duration);
    &:hover {
      background-color: rgba(env.$primary-color, .1);
    }
    &.active {
      background-color: rgba(env.$primary-color, .2);
    }

    h3 {
      font-size: 1rem;
      font-weight: 400;
      margin: 0;
    }

    img {
      display: block;
      aspect-ratio: 287 / 150;
      width: 100%;
      border-top-left-radius: inherit;
      border-top-right-radius: inherit;
    }

    .content {
      padding: 16px;
    }
  }

  .full {
    width: 100%;

    img {
      width: 100%;
    }

    h3 {
      font-size: 1.25rem;
      font-weight: 500;
      margin-bottom: 20px;
    }

    > .content {
      padding: 30px;
    }

    .meta {
      display: flex;
      gap: 20px;

      data, time {
        display: flex;
        align-items: center;
        gap: 8px;
      }
    }

    p {
      line-height: 1.7;
    }

    a {
      display: block;
      width: fit-content;
      margin-left: auto;
    }
  }
</style>