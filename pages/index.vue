<template>
  <div class="container">
    <h1 class="text-center">Курсы</h1>
    <div class="courses mt-30">
      <form class="courses-form form" id="filterform" role="form">
        <div>
          <my-select id="subj" placeholder="Все предметы">
            <option v-for="subject in subjects">{{ subject }}</option>
          </my-select>
        </div>
        <div>
          <my-select id="genre" placeholder="Все жанры">
            <option v-for="genre in genres">{{ genre }}</option>
          </my-select>
        </div>
        <div>
          <my-select id="grade" placeholder="Все классы">
            <option v-for="grade in grades">{{ grade }}</option>
          </my-select>
        </div>
        <div>
          <my-search placeholder="Поиск"></my-search>
        </div>
      </form>
    </div>
    <h1 v-show="isSearch" class="text-center search-info">Результаты поиска:</h1>
    <ul class="courses-list" v-bind:class="[isSearch ? '' : 'mt-60']">
      <li v-for="n in 7" class="courses-list-item">
        <div class="item-figure">
          <img src="https://www.imumk.ru/covers/80.png" alt="Алгебра">
          <div class="item-figure-link">
            <a href="#">Попробовать</a>
          </div>
        </div>
        <div class="item-info">
          <p class="item-title">Алгебра</p>
          <p class="item-grade">7 класс</p>
          <p class="item-genre">Рабочая тетрадь</p>
          <p class="item-meta"><a href="https://www.imumk.ru/course/80">Подробнее</a></p>
          <p class="item-controls">
            <a href="#" class="pure-button pure-button-primary btn-fluid js-purchase-offer" data-offer="103">Купить за 200 руб.</a>
          </p>
        </div>
      </li>

    </ul>
  </div>
</template>

<script>
  /* eslint-disable import/no-unresolved */

  import Logo from '~/components/Logo.vue';
  import MySelect from '~/components/MySelect.vue';
  import MySearch from '~/components/MySearch.vue';

  export default {
    components: {
      Logo,
      MySelect,
      MySearch,
    },
    data() {
      return {
        isSearch: false,
        subjects: [
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
        ],
        genres: [
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
        ],
        grades: [
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
        ],
      };
    },
  };
</script>

<style lang="scss">
  .mt-30 {
    margin-top: 30px;
  }

  a:active, a:hover {
    outline: 0;
  }

  .container {
    /*border: 1px solid black;*/
    background-color: linen;
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
      &.search-info {
        font-size: 24px;
      }
    }
  }

  .courses {
    overflow: hidden;
    padding: 0 15px;
    &-form {
      & > div {
        box-sizing: border-box;
        display: block;
        float: left;
        padding: 0 0 15px;
        width: 100%;
        @media screen and (min-width: 36em) {
          padding: 0 11px 15px;
          width: 33.3333%;
        }
        @media screen and (min-width: 48em) {
          padding: 0 11px;
          width: 25%;
        }
        &:first-child {
          padding-left: 0;
        }
        &:nth-child(3) {
          @media screen and (min-width: 36em) {
            padding-right: 0;
            width: 33.3333%;
          }
          @media screen and (min-width: 48em) {
            padding-right: 11px;
            width: 25%;
          }
        }
        &:last-child {
          @media screen and (min-width: 36em) {
            padding: 0 0 15px;
            width: 100%;
          }
          @media screen and (min-width: 48em) {
            padding-left: 11px;
            width: 25%;
          }
        }
      }

    }

  }

  .courses-list {
    overflow: hidden;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: flex-start;
    list-style: none;
    padding: 0;
    & &-item {
      float: left;
      box-sizing: border-box;
      overflow: hidden;
      display: block;
      margin: 0 15px 55px;
      width: 170px;
      min-height: 260px;
      border: solid 1px #b5b5b5;
      border-radius: 10px;
      background: #fff;
      .item-figure {
        position: relative;
        overflow: hidden;
        height: 134px;
        background: #ddd;
        img {
          max-width: 100%;
          border: 0;
        }
        &-link {
          position: absolute;
          bottom: 0;
          left: 0;
          box-sizing: border-box;
          padding: 7px 16px;
          width: 100%;
          background: rgba(0, 0, 0, 0.3);
          text-align: center;
          a {
            box-sizing: border-box;
            display: block;
            padding: .4em 1em .5em;
            font-size: 12px;
            font-weight: 600;
            text-align: center;
            text-decoration: none;
            line-height: normal;
            color: #00aee6;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 6px;
          }
        }
      }
      .item-info {
        padding: 10px 16px;
        & > p {
          margin: .4em 0;
          padding-left: .5em;
          font-size: 14px;
          font-weight: normal;
          color: #3c3c3b;
        }
        .item-title {
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          margin: 0;
        }
        .item-grade {
          margin-top: -.2em;
        }
        .item-genre {
          margin-top: -.4em;
          font-size: 11px;
        }
        .item-meta {
          margin-bottom: 0;
          font-size: 12px;
          font-weight: 600;
          color: #00c1ff;
          a {
            color: #00c1ff;
            text-decoration: none;
            background-color: transparent;
            &:hover {
              text-decoration: underline;
            }
          }
        }
        .item-controls {
          margin-bottom: 0;
          padding-left: 0;
          font-size: 12px;
          .pure-button {
            padding: .4em .1em;
            border-radius: 6px;
            background: #00c1ff;
            font-family: inherit;
            font-size: 100%;
            border: none transparent;
            text-decoration: none;
            display: inline-block;
            zoom: 1;
            line-height: normal;
            white-space: nowrap;
            vertical-align: middle;
            text-align: center;
            cursor: pointer;
            -webkit-user-drag: none;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
            box-sizing: border-box;
            &:hover {
              background: #00aee6;
            }
            &-primary {
              /*background-color: #0078e7;*/
              color: #fff;
            }
            &.btn-fluid {
              display: block;
            }
          }
        }

      }
    }
  }

  .mt-60 {
    margin-top: 60px;
  }

</style>
