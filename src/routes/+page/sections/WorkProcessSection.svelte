{#snippet sectionItem(numerator, title, textContent, right = false)}
  <div class="section-item" class:right>
    <div class="numerator">{numerator}</div>
    <div class="content">
      <h3>{title}</h3>
      <p>{textContent}</p>
      <hr>
    </div>
  </div>
{/snippet}

<section class="page-container">
  <h2>Процесс работы</h2>

  <div class="content">
    {@render sectionItem('01', 'Аудит', 'Проводим анализ проблемы, предлагаем решения, сроки и размер оплаты, всё что от вас требуется - описание проблемы')}
    {@render sectionItem('02', 'Решение и договор', 'По окончании аудита и согласия 2х сторон мы заключаем договор с предоплатой в 30%', true)}
    {@render sectionItem('03', 'Разработка', 'Далее наши специалисты. Все этапы работы вы сможете увидеть на нашей доске, а если этого мало, то информация о текущем состоянии будет предоствалена по первому требованию')}
    {@render sectionItem('04', 'Запуск и поддержка', 'Успешный запуск продукта не гарантирует его функциональность без ошибок. Наши специалисты будут ежедневно разрешать жалобы о возможных неисправностях', true)}
  </div>
</section>

<style lang="scss">
  @use "$lib/scss/mixins/scr";

  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  section > .content {
    @include scr.tablet-and-lower {
      margin-top: 40px;
      display: flex;
      flex-direction: column;
      gap: 36px;
    }
  }

  .section-item {
    position: relative;
    padding: 30px;
    display: flex;
    align-items: center;
    gap: 60px;

    @include scr.tablet-and-lower {
      padding: 0;
    }

    .numerator {
      width: 3ex;
      color: var(--primary-color);
      font-size: 6rem;
      font-weight: 600;
      font-family: "Unbounded", sans-serif;
      opacity: .2;

      @include scr.tablet-and-lower {
        position: absolute;
        bottom: 0;
        right: 0;
        font-size: 40px;
        opacity: .1;
        margin-bottom: 16px;
      }
    }

    .content {
      max-width: 735px;

      h3 {
        margin: 0;
      }

      p {
        line-height: 1.7;
        margin: 16px 0 0;

        color: var(--text-content-color);

        @include scr.tablet-and-lower {
          max-width: 253px;
        }
      }

      hr {
        border: none;
        max-width: 300px;
        margin-left: 0;
        height: 2px;
        margin-top: 16px;
        margin-bottom: 0;
        background-color: var(--primary-color);
        @include scr.tablet-and-lower {
          max-width: 140px;
        }
      }
    }

    @include scr.laptop-and-higher {
      &.right {
        flex-direction: row-reverse;
        text-align: right;

        .content hr {
          margin-right: 0;
          margin-left: auto;
        }
      }
    }
  }

</style>