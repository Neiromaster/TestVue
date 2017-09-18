<template>
  <div class="courses-list-item">
    <div class="item-figure">
      <img :src="'https://www.imumk.ru/covers/' + course.courseId + '.png'" alt="Алгебра">
      <div v-show="course.status === ''" class="item-figure-link">
        <a href="#">Попробовать</a>
      </div>
    </div>
    <div class="item-info">
      <p class="item-title">{{ course.subject }}</p>
      <p class="item-grade">{{ grade }}</p>
      <p class="item-genre">{{ course.genre }}</p>
      <p class="item-meta"><a :href="course.shopUrl ? course.shopUrl : '#'">{{ course.price > 0 ? 'Подробнее'
        : 'Перейти к обучению'}}</a></p>
      <p class="item-controls">
        <a href="#" class="pure-button pure-button-primary btn-fluid js-purchase-offer"
           data-offer="103">{{ payment }}</a>
      </p>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      course: Object,
    },
    computed: {
      grade() {
        const grades = this.course.grade.split(';');
        return `${grades.join('-')} ${grades.length > 1 ? 'классы' : 'класс'}`;
      },
      payment() {
        if (this.course.price > 0) {
          return `Купить за ${this.course.price} руб.`;
        }
        return 'Подробнее';
      },
    },
  };
</script>

<style lang="scss">
  .courses-list-item {
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
</style>
