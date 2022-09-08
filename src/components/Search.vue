<template>
    <input type="text" @input="search" class="search">
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Search",
  methods: {
    search(event) {
      this.$emit('search', event.target.value)
    }
  }
};
</script>

<style scoped>
.search {
  margin-bottom: 30px;
}
</style>
