<script>
  import Button from "$lib/components/Button.svelte"
</script>

<section>
  <div class="form-wrapper">
    <h2>Свяжитесь с нами</h2>
    <p>Наш менеджер проконсультирует вас по любому вопросу в течении 24 часов</p>

    <form action="">
      <input placeholder="Имя" type="text">
      <input placeholder="Телефон для связи" type="text">
      <input placeholder="Предпочитаемый мессенджер" type="text">
      <input placeholder="https://t.me/..." type="text">
      <input placeholder="Интересующая вас услуга" type="text">
      <Button type="submit">Получить консультацию</Button>
    </form>

    <div class="policy">
      Нажимая на кнопку вы соглашаетесь с <a class="active" href="#">политикой конфиденциальности</a>
      и даете <a class="active" href="#">согласие на обработку персональных данных</a>
    </div>
  </div>
</section>

<style lang="scss">
  section {
    padding-top: var(--section-padding-y);
    padding-bottom: var(--section-padding-y);
  }

  .form-wrapper {
    --btn-width: 100%;
    background-color: var(--bg-color);
    border: 1px solid #EBEBEB;
    padding: 60px;
    border-radius: 30px;

    max-width: 780px;
    width: 100%;
    margin-left: auto;
    margin-right: auto;


    h2 {
      margin: 0;
    }
    p {
      margin: 30px 0;
      color: var(--text-content-color);
    }
  }


  form {
    display: flex;
    flex-direction: column;
    gap: 20px;
    font-size: 18px;
  }

  input {
    width: 100%;
    padding: 16px 30px;
    background-color: var(--block-bg-color);
    border-radius: 10rem;
    border: none;
    outline: none;
    font: inherit;
  }

  .policy {
    margin-top: 30px;
  }
</style>