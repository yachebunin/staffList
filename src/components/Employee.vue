<template>
  <div class="employee">
    <div>{{ index + 1 }}</div>
    <div class="name">{{ this.employee.first_name || 'Нет имени' }}</div>
    <div class="surname">{{ this.employee.last_name || 'Нет фамилии' }}</div>
    <div class="email">{{ this.employee.email || 'Нет почты' }}</div>
    <div class="profile-link">{{ this.employee.profile_link || 'Нет ссылки' }}</div>
    <div class="pay-status">{{ this.employee.pay_status ? 'Да' : 'Нет' }}</div>
    <div class="username">{{ this.employee.username || 'Нет логина' }}</div>

    <div>
      <button @click="$emit('set-change-index', index)" class="change">
        Изменить
      </button>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Employee",
  props: ["employee", "index"],
};
</script>

<style scoped>
.employee {
  display: flex;
  justify-content: space-between;
}

.employee:not(:last-child) {
  margin-bottom: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid #fff;
}

.employee > div {
  width: 16.6%;
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
}

.employee > div:first-child {
  width: 7%;
}

.profile-link {
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
