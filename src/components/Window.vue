<template>
  <div class="window">
    <div class="label">
      <span>ФИО: </span>
      <input v-model="employeeData.name" class="name" type="text" />
    </div>
    <div class="label">
      <span>Компания: </span>
      <input v-model="employeeData.company" class="company" type="text" />
    </div>
    <div class="label">
      <span>Направление: </span>
      <input v-model="employeeData.department" class="department" type="text" />
    </div>
    <div class="label">
      <span>Должность: </span>
      <input v-model="employeeData.position" class="position" type="text" />
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
        name: "",
        company: "",
        department: "",
        position: "",
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
