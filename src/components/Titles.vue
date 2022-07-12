<template>
  <div class="titles">
    <div @click="$emit('filter')" class="filter">filter</div>
    <div class="name">ФИО</div>
    <div class="company">Компания</div>
    <div class="department">Направление</div>
    <div class="position">Должность</div>
    <div></div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Titles",
};
</script>

<style scoped>
.titles {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  padding-bottom: 5px;
  border-bottom: 1px solid #fff;
}

.titles > div {
  width: 16.6%;
}

.titles > div:first-child {
  width: 7%;
}

.filter:hover {
  font-weight: bold;
  cursor: pointer;
}
</style>
