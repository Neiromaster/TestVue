<template>
  <div class="search-box">
    <input type="text" :placeholder="placeholder" id="search" name="search" :value="pattern" @input="input">
    <button class="search-box-search-btn" type="submit" title="Найти"></button>
  </div>
</template>

<script>
  export default {
    name: 'my-select',
    props: {
      value: {
        type: [String, Number, Boolean, Object, Array, Symbol, Function],
        default: null,
      },
      placeholder: String,
      pattern: String,
    },
    data() {
      return {
        text: this.value,
      };
    },
    watch: {},
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

  .search-box {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    &-search-btn {
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
