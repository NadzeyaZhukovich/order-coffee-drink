<template>
  <div>
    <select name="sort" v-model="selected">
      <option>sort A-Z</option>
      <option>sort Z-A</option>
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
