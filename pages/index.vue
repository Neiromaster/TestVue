<template>
  <div class="container">
    <h1 class="text-center">Курсы</h1>
    <div class="courses mt-30">
      <form class="courses-form form" id="filterform" role="form">
        <div>
          <my-select id="subj" placeholder="Все предметы" v-model="choiceSubj">
            <option v-for="subject in subjects">{{ subject }}</option>
          </my-select>
        </div>
        <div>
          <my-select id="genre" placeholder="Все жанры" v-model="choiceGenre">
            <option v-for="genre in genres">{{ genre }}</option>
          </my-select>
        </div>
        <div>
          <my-select id="grade" placeholder="Все классы" v-model="choiceGrade">
            <option v-for="grade in 11">{{ grade }}</option>
          </my-select>
        </div>
        <div>
          <my-search placeholder="Поиск" @search="searchText"></my-search>
        </div>
      </form>
    </div>
    <h1 v-show="isSearch" class="text-center search-info">Результаты поиска:</h1>
    <ul class="courses-list" v-bind:class="[isSearch ? '' : 'mt-60']">
      <li v-for="course in courses">
        <course-item :course="course"></course-item>
      </li>
    </ul>
  </div>
</template>

<script>
  /* eslint-disable import/no-unresolved */

  import Logo from '~/components/Logo.vue';
  import MySelect from '~/components/MySelect.vue';
  import MySearch from '~/components/MySearch.vue';
  import CourseItem from '~/components/CourseItem.vue';
  import axios from 'axios';

  export default {
    data() {
      axios.post('http://api.qa.imumk.ru/api/mobilev1/update', { data: '' })
        .then(this.getCourses)
        .catch((error) => {
          console.log(error);
        });
      return {
        isSearch: false,
        searchedText: '',
        choiceSubj: '',
        choiceGenre: '',
        choiceGrade: '',
        originalCourses: [],
        subjects: [],
        genres: [
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
          'asewqrqw',
        ],
      };
    },
    components: {
      Logo,
      MySelect,
      MySearch,
      CourseItem,
    },
    methods: {
      getCourses(response) {
        this.originalCourses = response.data.items.map((t) => {
          const o = Object.create(t);
          o.searchCache = `${o.title} ${o.genre} ${o.subject} ${o.description} ${o.price}`.toLowerCase();
          return o;
        });
        this.subjects = this.originalCourses.map(e => e.subject)
          .filter((value, index, self) => self.indexOf(value) === index)
          .sort((a, b) => a.localeCompare(b));
        this.genres = this.originalCourses.map(e => e.genre)
          .filter((value, index, self) => self.indexOf(value) === index)
          .sort((a, b) => a.localeCompare(b));
      },

      searchText(text) {
        this.searchedText = text;
      },

      sortedUnique(arr) {
        const res = [];
        arr.values().forEach((item) => {
          if (res.indexOf(item) < 0) res.push(item);
        });
        return arr.sort((a, b) => a.localeCompare(b));
      },
    },
    computed: {
      courses() {
        const vm = this;
        return this.originalCourses ? this.originalCourses.filter(course =>
          (vm.choiceSubj ? course.subject === vm.choiceSubj : true) &&
          (vm.choiceGrade ? course.grade === vm.choiceGrade : true) &&
          (vm.choiceGenre ? course.genre === vm.choiceGenre : true) &&
          course.searchCache.indexOf(vm.searchedText.toLowerCase()) !== -1) : [];
      },
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
  }

  .mt-60 {
    margin-top: 60px;
  }

</style>
