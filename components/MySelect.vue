<template>
  <select v-model="selected">
    <option
      v-if="placeholder"
      :value="null"
      selected
    >
      {{ placeholder }}
    </option>
    <slot></slot>
  </select>
</template>

<script>
  export default {
    name: 'my-select',
    props: {
      value: {
        type: [String, Number, Boolean, Object, Array, Symbol, Function],
        default: null,
      },
      items: [String, Array],
      placeholder: String,
    },
    data() {
      return {
        selected: this.value,
      };
    },
    watch: {
      value(value) {
        this.selected = value;
      },
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

