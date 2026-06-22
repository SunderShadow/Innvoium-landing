<script lang="ts">
  let openI = $state(0)
</script>

<section id="FAQ" class="page-container">
  <h2>Частые вопросы</h2>

  <div class="content">
    <div class="questions">
      {#each Array(4) as _, i (i)}
        <div class="question" class:open={openI == i} onclick={() => {openI = i}}>
          <h3>Текст вопроса</h3>
          <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
        </div>
      {/each}
    </div>
    <div class="contact">
      <h3>Остались вопросы?</h3>
      <p>
        Пишите нам — ответим на все вопросы.
        <br>
        <b>ПН-ПТ с 9:00 до 21:00 по МСК</b>
      </p>
      <div class="icons">
        <a href="">
          <svg width="35" height="35" viewBox="0 0 35 35" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g clip-path="url(#clip0_1525_1722)">
              <path d="M17.1293 0.676278C6.989 1.20614 0.295249 9.15892 0.718165 19.1874C0.902888 23.577 2.66747 27.3541 3.08553 31.52C3.19247 32.5992 2.88136 33.9311 4.1258 34.4027C5.65705 34.9811 8.00497 34.0089 9.2883 33.1193C9.7258 32.8228 10.1439 32.4777 10.4647 32.0499C11.7918 32.9298 13.0508 33.7804 14.6307 34.1596C21.5869 35.827 29.2091 32.011 32.5973 25.8811C38.9654 14.3652 30.3564 -0.0139998 17.1293 0.676278ZM13.1918 24.7096C12.6425 25.1374 12.1126 25.7207 11.505 26.0561C10.6251 26.5277 10.3529 26.0367 10.0223 25.2589C8.98205 22.7846 8.85567 18.57 9.4633 15.9791C10.28 12.4548 13.0071 9.35336 16.755 9.02281C20.5466 8.68739 24.0661 10.6124 25.6557 14.0881C29.1751 21.8221 20.1675 29.4589 13.1918 24.7145V24.7096Z" fill="#1A1D29"/>
            </g>
            <defs>
              <clipPath id="clip0_1525_1722">
                <rect width="35" height="35" fill="white"/>
              </clipPath>
            </defs>
          </svg>
        </a>

        <a href="">
          <svg width="35" height="35" viewBox="0 0 35 35" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd" clip-rule="evenodd" d="M28.841 6.46037C29.2014 6.30869 29.5959 6.25637 29.9833 6.30887C30.3708 6.36137 30.7371 6.51676 31.0441 6.75887C31.3512 7.00097 31.5877 7.32095 31.7291 7.68549C31.8705 8.05002 31.9116 8.4458 31.8481 8.83162L28.5406 28.8939C28.2198 30.8291 26.0965 31.9389 24.3217 30.975C22.8371 30.1685 20.6321 28.926 18.6487 27.6295C17.6571 26.9806 14.6194 24.9025 14.9927 23.4237C15.3135 22.1593 20.4177 17.4081 23.3344 14.5833C24.4792 13.4735 23.9571 12.8333 22.6052 13.8541C19.2481 16.3887 13.8581 20.2431 12.076 21.3281C10.504 22.2847 9.68437 22.4481 8.70437 22.2847C6.91645 21.9872 5.25833 21.5264 3.90499 20.965C2.07624 20.2066 2.1652 17.6924 3.90353 16.9604L28.841 6.46037Z" fill="#1E1E1E"/>
          </svg>
        </a>

      </div>
    </div>
  </div>
</section>

<style lang="scss">
  section > .content {
    display: flex;
    gap: 30px;
  }

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  .questions {
    display: flex;
    flex-direction: column;
    gap: 30px;
  }

  .question {
    padding: 30px;
    border-radius: 30px;
    background: var(--block-bg-color);

    cursor: pointer;

    h3 {
      margin: 0;
    }
    p {
      height: 0;
      overflow: hidden;
      margin: 0;
      transition-property: margin, height;
      transition-duration: var(--transition-duration);
    }

    &.open {
      p {
        margin-top: 20px;
        height: 110px;
      }
    }
  }

  .contact {
    flex-shrink: 0;
    width: 390px;
    height: fit-content;
    background-color: var(--primary-color);
    padding: 30px;
    border-radius: 30px;

    font-size: 20px;
    color: #FFF;

    line-height: 1.7;

    h3 {
      margin: 0;
      font-size: 1.5rem;
    }

    .icons {
      display: flex;
      gap: 12px;

      > a {
        display: flex;
        background-color: #FFF;
        padding: 12px;
        border-radius: 10rem;
      }
    }
  }
</style>