<template>
  <div class="controller">
    <button @click="$emit('show-add-window')" class="add">добавить</button>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Controller",
};
</script>

<style scoped>
.controller {
  margin-bottom: 20px;
}
</style>
