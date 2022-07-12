<template>
  <div class="employee">
    <div>{{ index + 1 }}</div>
    <div class="name">{{ this.employee.name }}</div>
    <div class="company">{{ this.employee.company }}</div>
    <div class="department">{{ this.employee.department }}</div>
    <div class="position">{{ this.employee.position }}</div>

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
}

.employee > div:first-child {
  width: 7%;
}
</style>
