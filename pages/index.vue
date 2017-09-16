<template>
  <section class="container">
    <h1 class="text-center">Курсы</h1>
    <div class="courses mt-30">
      <form class="courses-form form" id="filterform" role="form">
        <div>
          <select id="subj" name="subj">
            <option value="">Все предметы</option>
            <option>Алгебра</option>
            <option>Английский язык</option>
            <option>Биология</option>
            <option>География</option>
            <option>Геометрия</option>
            <option>Демо-версия</option>
            <option>Естествознание</option>
            <option>Информатика</option>
            <option>История</option>
            <option>Математика</option>
            <option>Обществознание</option>
            <option>Окружающий мир</option>
            <option>Русский язык</option>
            <option>Физика</option>
            <option>Химия</option>
          </select>
        </div>
        <div>
          <select id="genre" name="genre">
            <option value="">Все жанры</option>
            <option>Задачник</option>
            <option>Медиа-коллекция</option>
            <option>Рабочая тетрадь</option>
            <option>Тренажер ВПР-2017</option>
            <option>Тренажер ЕГЭ-2016</option>
            <option>Тренажер ЕГЭ-2017</option>
          </select>
        </div>
        <div>
          <select id="grade" name="grade">
            <option value="">Все классы</option>
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
            <option>6</option>
            <option>7</option>
            <option>8</option>
            <option>9</option>
            <option>10</option>
            <option>11</option>
          </select>
        </div>
        <div>
          <input class="borderFind" type="text" placeholder="Поиск" id="search" name="search">
          <button class="courses-form-search-btn" type="submit" title="Найти"></button>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
  // eslint-disable-next-line import/no-unresolved
  import Logo from '~/components/Logo.vue';

  export default {
    components: {
      Logo,
    },
  };
</script>

<style lang="scss">
  .container {
    overflow: hidden;
    margin: 0 auto;
    padding: 0;
    max-width: 1000px;
    .text-center {
      text-align: center;
    }

    h1 {
      font-weight: 300;
      font-size: 32px;
      color: #3c3c3b;
      @media screen and (min-width: 48em) {
        font-size: 36px;
      }
    }
  }

  .mt-30 {
    margin-top: 30px;
  }

  .courses {
    overflow: hidden;
  }

  .courses-form {
    input[type="text"], select {
      width: 100%;
    }
    div {
      float: left;
      width: 25%;
    }
  }

  .courses-form-search-btn {
    overflow: visible;
  }

  .courses-form > div:last-child {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
  }
</style>
