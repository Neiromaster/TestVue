<template>
  <div class="search-field">
    <input type="text"
           :placeholder="placeholder"
           v-model="searchText"
           @focus="selectAll">
    <button class="search-btn"
            @click.prevent="runSearch"
            title="Найти"></button>
  </div>
</template>

<script>
  export default {
    name: 'my-select',
    props: {
      placeholder: String,
    },
    data() {
      return {
        searchText: '',
      };
    },
    methods: {
      runSearch() {
        this.$emit('search', this.searchText);
      },
      selectAll(event) {
        // Workaround for Safari bug
        // http://stackoverflow.com/questions/1269722/selecting-text-on-focus-using-jquery-not-working-in-safari-and-chrome
        setTimeout(() => {
          event.target.select();
        }, 0);
      },
    },
  };
</script>

<style lang="scss">
  input {
    width: 100%;
    padding: .3em .5em;
    height: 2.3em;
    background-color: #fff;
    &:focus {
      border-color: #129FEA;
    }
  }

  .search-field {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    .search-btn {
      overflow: visible;
      width: 32px;
      height: 32px;
      line-height: normal;
      background: #fff url('https://www.imumk.ru/Content/skins/bubble/images/icons/icon-search-25.png') center no-repeat;
      border: 0;
      border-radius: 4px;
    }
  }
</style>
