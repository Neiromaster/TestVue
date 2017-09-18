<template>
  <select v-model="selected">
    <option
      v-if="placeholder"
      value=""
      selected>
      {{ placeholder }}
    </option>
    <slot></slot>
  </select>
</template>

<script>
  export default {
    name: 'my-select',
    props: {
      items: [String, Array],
      placeholder: String,
    },
    data() {
      return {
        selected: '',
      };
    },
    methods: {},
    watch: {
      selected(value) {
        this.$emit('input', value);
      },
    },
  };
</script>

<style lang="scss">
  select {
    width: 100%;
    padding: .3em .5em;
    height: 2.3em;
    background-color: #fff;
    &:focus {
      border-color: #129FEA;
    }
  }
</style>

