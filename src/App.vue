<template>
  <div id="app">
    <Controller @show-add-window="isShowAddWindow = true" />
    <Table @filter="filter" @set-change-index="setChangeIndex" :staff="staff" />
    <Window :action="addEmployee" v-if="isShowAddWindow" />
    <Window
      :action="changeEmployee"
      :dataEmployee="staff[changeIndex]"
      v-if="isShowChangeWindow"
    />

    <div v-if="isShowAddWindow || isShowChangeWindow" class="background"></div>
  </div>
</template>

<script>
import Controller from "./components/Controller";
import Table from "./components/Table";
import Window from "./components/Window";

export default {
  name: "App",
  data() {
    return {
      isShowAddWindow: false,
      isShowChangeWindow: false,
      changeIndex: 0,
      staff: [
        {
          name: "Иван Иванов",
          company: "Google",
          department: "Разработка внутреннего ПО",
          position: "Руководитель",
        },
      ],
    };
  },
  components: {
    Controller,
    Table,
    Window,
  },
  methods: {
    setChangeIndex(index) {
      this.changeIndex = index;
      this.isShowChangeWindow = true;
    },
    addEmployee(employee) {
      let isEmpty = true;

      for (const key in employee) {
        if (employee[key]) {
          isEmpty = false;
        }
      }

      !isEmpty && this.staff.push(employee);
      this.isShowAddWindow = false;
    },
    changeEmployee(employee) {
      this.staff.splice(this.changeIndex, 1, employee);
      this.isShowChangeWindow = false;
    },
    filter() {
      this.staff = this.staff.sort((first, second) => {
        if (first.name < second.name) {
          return -1;
        }

        if (first.name > second.name) {
          return 1;
        }

        return 0;
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.background {
  position: absolute;
  left: 0px;
  top: 0px;
  background: rgba(0, 0, 0, 0.7);
  min-height: 100%;
  min-width: 100%;
  z-index: 1;
}

button {
  padding: 7px;
  border: 1px solid #fff;
  background: #000;
  color: #fff;
}

button:hover {
  background: orange;
  cursor: pointer;
}
</style>
