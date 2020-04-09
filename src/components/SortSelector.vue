<template>
  <div class="sort-selector">
    <select class="sort-selector__selector"
            name="sort"
            v-model="selected">
      <option class="sort-selector__option">sort A-Z</option>
      <option class="sort-selector__option">sort Z-A</option>
    </select>
  </div>

</template>

<script>
  export default {
    name: 'SortSelector',
    data() {
      return {
        selected: 'sort A-Z',
      }
    },
    watch: {
      selected() {
        if(this.selected === 'sort A-Z') {
          this.$emit('sort', 'A-Z');
        } else {
          this.$emit('sort', 'Z-A');
        }
      }
    }
  }
</script>

<style>
  .sort-selector__selector {
    width: 100px;
    padding: 3px;
    border: none;

    background: transparent;
    color: #ffffff;
    font-size: 16px;
    text-transform: capitalize;
  }
</style>
