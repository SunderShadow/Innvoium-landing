<script lang="ts">
  import bgImgDesktop from "../assets/header-section-bg.png?enhanced&format=webp"
  import bgImgMobile from "../assets/header-section-bg-mobile.png?enhanced&format=webp"
  import Button from "$lib/components/Button.svelte"
  import * as Form from "$lib/components/Form.svelte"
</script>

<svelte:head>
  <link rel="preload" as="image" href={bgImgDesktop.img.src} fetchpriority="high">
</svelte:head>

  <section class="page-container" id="header-section" style:--bg-img-desktop="url('{bgImgDesktop.img.src}')" style:--bg-img-mobile="url('{bgImgMobile.img.src}')">
  <h1>
    Автоматизируем рутину вашего бизнеса за 30 дней<br>
    <span>от анализа до запуска под ключ</span>
  </h1>

  <p>Нейроворонки, чат-боты, CRM, интеграция ИИ <br>и другие цифровые сервисы</p>
  <Button href="#cases">Наши кейсы</Button>

  <form>
    <h2>Обсудим проект?</h2>
    <Form.Input placeholder="Имя">
      {#snippet svg()}
        <svg width="18" height="19" viewBox="0 0 18 19" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M13 11.2002C15.7598 11.2004 18 13.2913 18 15.8672V17.7334C18 18.2466 17.5498 18.6668 17 18.667C16.45 18.667 16 18.2467 16 17.7334V15.8672C16 14.3273 14.6498 13.0675 13 13.0674H5C3.35004 13.0674 2 14.3272 2 15.8672V17.7334C2 18.2467 1.54998 18.667 1 18.667C0.450013 18.667 0 18.2467 0 17.7334V15.8672C0 13.2912 2.24007 11.2002 5 11.2002H13ZM9 0C11.7598 0.000134037 14 2.09109 14 4.66699C13.9998 7.24273 11.7597 9.33287 9 9.33301C6.24019 9.33301 4.0002 7.24282 4 4.66699C4 2.09101 6.24007 0 9 0ZM9 1.86621C7.35004 1.86621 6 3.127 6 4.66699C6.00021 6.20682 7.35017 7.4668 9 7.4668C10.6497 7.46666 11.9998 6.20674 12 4.66699C12 3.12708 10.6498 1.86635 9 1.86621Z" fill="#4C4C4C"/>
        </svg>
      {/snippet}
    </Form.Input>
    <Form.Input placeholder="Телефон для связи">
      {#snippet svg()}
        <svg width="18" height="19" viewBox="0 0 18 19" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M14.8407 18.0368C14.7777 18.0368 14.7069 18.0368 14.644 18.0289C12.103 17.7536 9.63288 16.8725 7.50099 15.488C5.51857 14.2293 3.80363 12.5144 2.54495 10.5319C1.16041 8.3922 0.279331 5.91418 0.0118623 3.37322C-0.0510716 2.72815 0.13773 2.11454 0.5468 1.63467C0.948003 1.14694 1.52227 0.855866 2.14375 0.792932C2.21455 0.785066 2.28535 0.785066 2.35615 0.785066H4.71617C4.72403 0.785066 4.7319 0.785066 4.73977 0.785066C5.90404 0.785066 6.90312 1.65041 7.06832 2.81468C7.16272 3.51482 7.33579 4.19923 7.57966 4.86003C7.90219 5.71751 7.69766 6.69298 7.04472 7.34592L6.47832 7.91232C7.40659 9.3598 8.6338 10.5949 10.0891 11.5232L10.6556 10.9567C11.3085 10.3117 12.2918 10.0993 13.1493 10.4218C13.8022 10.6657 14.4945 10.8387 15.1868 10.9253C16.3747 11.0905 17.2479 12.121 17.2243 13.3089V15.6611C17.2243 16.2904 16.9804 16.8804 16.5399 17.3288C16.0993 17.7772 15.5015 18.0211 14.8721 18.0289C14.8564 18.0368 14.8485 18.0368 14.8407 18.0368ZM4.7319 2.35841C4.72403 2.35841 4.72403 2.35841 4.7319 2.35841H2.35615C2.07295 2.38201 1.88414 2.47641 1.75041 2.64161C1.61668 2.79895 1.55374 3.00348 1.56948 3.21589C1.81334 5.50511 2.60788 7.73926 3.86656 9.68234C5.00724 11.476 6.55698 13.0257 8.3506 14.1664C10.2858 15.4251 12.52 16.2117 14.8013 16.4635C15.0767 16.4949 15.2655 16.3848 15.4149 16.2353C15.5644 16.0859 15.6431 15.8892 15.6431 15.6768V13.3168C15.6431 13.3089 15.6431 13.301 15.6431 13.2932C15.6509 12.892 15.3599 12.5537 14.9665 12.4986C14.1641 12.3964 13.3617 12.1918 12.5908 11.9086C12.2997 11.7985 11.9772 11.8693 11.7569 12.0817L10.7578 13.0808C10.5061 13.3325 10.1206 13.3797 9.81381 13.2066C7.72126 12.0188 5.99058 10.2802 4.8027 8.19553C4.62963 7.88872 4.67683 7.50325 4.92857 7.25152L5.92764 6.25244C6.14005 6.02431 6.21085 5.70177 6.10071 5.4107C5.80964 4.63976 5.61298 3.83736 5.50284 3.02708C5.45564 2.64948 5.11737 2.35841 4.7319 2.35841ZM14.0697 7.82579C13.7 7.82579 13.3696 7.56619 13.2988 7.18859C13.0549 5.92204 12.0794 4.94657 10.8129 4.7027C10.3881 4.61616 10.1049 4.20709 10.1914 3.78229C10.2779 3.35749 10.687 3.07428 11.1118 3.16082C13.0077 3.53056 14.4709 4.99377 14.8407 6.88965C14.9272 7.31445 14.644 7.73139 14.2192 7.81006C14.1641 7.81792 14.1169 7.82579 14.0697 7.82579ZM17.2164 7.81792C16.8231 7.81792 16.4769 7.51899 16.4376 7.11778C16.1072 4.17563 13.818 1.89427 10.8758 1.56387C10.4431 1.51667 10.1363 1.12334 10.1835 0.698532C10.2307 0.265861 10.632 -0.0488079 11.0489 0.00625924C14.7305 0.415329 17.5861 3.27095 17.9952 6.94472C18.0424 7.37739 17.7356 7.76286 17.3029 7.81792C17.2715 7.81792 17.24 7.81792 17.2164 7.81792Z" fill="#4C4C4C"/>
        </svg>
      {/snippet}
    </Form.Input>

    <Button>Получить консультацию</Button>
    <p>
      Нажимая на кнопку вы соглашаетесь с <a class="active" href="/">политикой конфиденциальности</a> и даете согласие на
      <a class="active" href="/">обработку персональных данных</a>
    </p>
  </form>
</section>

<style lang="scss">
  @use "$lib/scss/env";
  @use "$lib/scss/mixins/scr";

  section {
    position: relative;
    min-height: 768px;
    background-image: var(--bg-img-desktop);
    background-size: cover;
    padding-top: 100px;

    --btn-width: 412px;

    @include scr.tablet-and-lower {
      background-image: var(--bg-img-mobile);
      background-size: cover;
      background-position: top left;
      padding-top: 40px;
      --btn-width: 172px;
      --btn-padding-y: 8px;
    }
  }

  section > p {
    margin-top: 46px;
    margin-bottom: 46px;

    @include scr.tablet-and-lower {
      max-width: 211px;
      br {
        display: none;
      }
    }
  }

  h1 {
    max-width: 730px;
    margin: 0;
    font-weight: 600;

    span {
      display: block;
      font-size: 40px;
      font-weight: 400;
      margin-top: 20px;
      color: var(--primary-color);

      @include scr.tablet-and-lower {
        font-size: 20px;
      }
    }
  }

  form {
    --btn-width: 100%;

    @include scr.laptop-and-higher {
      position: absolute;
      right: 142px;
      top: 50%;
      transform: translateY(-50%);
      width: 390px;
    }

    display: flex;
    flex-direction: column;
    gap: 20px;

    padding: 30px;

    background-color: rgba(#FAC9FF, .25);
    border-radius: 30px;
    border: 1px solid #D3D3D3;
    backdrop-filter: blur(8px);


    @include scr.tablet-and-lower {
      margin-top: 40px;
      gap: 12px;
    }


    h2, p {
      margin: 0;
    }

    h2 {
      font-size: 24px;
      text-align: center;

      @include scr.tablet-and-lower {
        font-size: 20px
      }
    }

    p {
      font-size: 12px;
    }
  }
</style>