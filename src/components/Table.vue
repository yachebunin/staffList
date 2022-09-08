<template>
  <div class="table">
    <Titles @filter="filter" />
    <Employee
      @set-change-index="setChangeIndex"
      :employee="employee"
      :staff="staff"
      :index="index"
      v-for="(employee, index) in staff"
      :key="employee.id"
    />
  </div>
</template>

<script>
import Titles from "./Titles.vue";
import Employee from "./Employee.vue";

export default {
  // eslint-disable-next-line
  name: "Table",
  props: ["staff"],
  components: {
    Titles,
    Employee,
  },
  methods: {
    setChangeIndex(index) {
      this.$emit("set-change-index", index);
    },
    filter(filt) {
      this.$emit('filter', filt)
    }
  },
};
</script>

<style scoped>
.table {
  margin-bottom: 20px;
  padding: 10px;
  background: #000;
  color: #fff;
}
</style>
