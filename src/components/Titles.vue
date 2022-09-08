<template>
  <div class="titles">
    <div @click="$emit('filter', 'number')">#</div>
    <div @click="$emit('filter', 'first_name')">Имя</div>
    <div @click="$emit('filter', 'last_name')">Фамилия</div>
    <div @click="$emit('filter', 'email')">email</div>
    <div @click="$emit('filter', 'profile_link')">Ссылка</div>
    <div @click="$emit('filter', 'pay_status')">Оплатил</div>
    <div @click="$emit('filter', 'username')">Логин</div>
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
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
}

.titles > div:not(:last-child) {
  cursor: pointer
}

.titles > div:first-child {
  width: 7%;
  cursor: none;
}
</style>
