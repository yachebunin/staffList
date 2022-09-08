<template>
  <div class="window">
    <div class="label">
      <span>email: </span>
      <input v-model="employeeData.email" class="email" type="text" />
    </div>
    <div class="label">
      <span>Имя: </span>
      <input v-model="employeeData.first_name" class="first_name" type="text" />
    </div>
    <div class="label">
      <span>Фамилия: </span>
      <input v-model="employeeData.last_name" class="last_name" type="text" />
    </div>
    <div class="label">
      <span>Логин: </span>
      <input v-model="employeeData.username" class="username" type="text" />
    </div>
    <div class="label">
      <span>Ссылка: </span>
      <input v-model="employeeData.profile_link" class="profile_link" type="text" />
    </div>
    <div class="label">
      <span>Оплатил(а): </span>
      <input v-model="employeeData.pay_status" type="checkbox" class="profile_link" />
    </div>

    <button @click="action(employeeData)" class="done">Готово</button>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Window",
  props: ["employee", "action", "dataEmployee"],
  mounted() {
    if (this.dataEmployee) {
      Object.assign(this.employeeData, this.dataEmployee);
    }
  },
  data() {
    return {
      employeeData: {
        email: "",
        first_name: "",
        last_name: "",
        username: "",
        profile_link: "",
        pay_status: false
      },
    };
  },
};
</script>

<style scoped>
.window {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: 20px;
  background: #000;
  color: #fff;
  border: 1px solid #fff;
  z-index: 2;
}

.window > .label {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}

.label > input {
  margin-left: 10px;
}
</style>
