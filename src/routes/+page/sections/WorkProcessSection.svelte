{#snippet sectionItem(numerator, title, textContent)}
  <div class="section-item">
    <div class="numerator">{numerator}</div>
    <div class="content">
      <h3>{title}</h3>
      <p>{textContent}</p>
    </div>
  </div>
{/snippet}

<section class="page-container">
  <h2>Процесс работы</h2>

  <div class="content">
    {@render sectionItem('01', 'Аудит', 'Проводим анализ проблемы, предлагаем решения, сроки и размер оплаты, всё что от вас требуется - описание проблемы')}
    {@render sectionItem('02', 'Решение и договор', 'По окончании аудита и согласия 2х сторон мы заключаем договор с предоплатой в 20%')}
    {@render sectionItem('03', 'Разработка', 'Дальше идут в бой наши специалисты. Все этапы работы вы сможете увидеть на нашей доске, а если этого мало, то информация о текущем состоянии будет предоствалена по первому требованию')}
    {@render sectionItem('04', 'Запуск и поддержка', 'Успешный запуск продукта не гарантирует его функциональность без ошибок. Наши специалисты будут ежедневно разрешать жалобы о возможных неисправностях, пресекая вашу тревогу')}
  </div>
</section>

<style lang="scss">
  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }
  .section-item {
    padding: 30px;
    display: flex;
    align-items: center;
    gap: 60px;

    .numerator {
      color: var(--primary-color);
      font-size: 6rem;
      font-weight: 600;
      font-family: "Unbounded", sans-serif;
    }

    .content {
      max-width: 735px;

      h3 {
        margin: 0;
      }

      p {
        line-height: 1.7;
        margin: 30px 0 0;

        color: var(--text-content-color);
      }
    }
  }

  section > .content {
    > *:nth-child(2) {
      margin-left: 60px;
    }

    > *:nth-child(3) {
      margin-left: 120px;
    }

    > *:nth-child(4) {
      margin-left: 180px;
    }
  }
</style>