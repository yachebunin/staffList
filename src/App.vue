<template>
  <div id="app">
    <Search @search="search" />
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
import Search from "./components/Search";

export default {
  name: "App",
  data() {
    return {
      isShowAddWindow: false,
      isShowChangeWindow: false,
      changeIndex: 0,
      oldStaff: null,
      staff: [
        {
          "id": 14,
          "email": "antonida@mail.com",
          "first_name": "Antonida",
          "pay_status": false,
          "last_name": "White",
          "username": "AntonidaW",
          "profile_link": "https://fizikl.ru/"
        },
        {
          "id": 17,
          "email": "butonchick@gmail.com",
          "first_name": "",
          "pay_status": true,
          "last_name": "Zorro",
          "username": "ananimus007",
          "profile_link": "https://translate.google.com/?sl=de&tl=ru&text=Herzlich%20willkommen!&op=translate"
        },
        {
          "id": 8,
          "email": "vasya2007@mail.ru",
          "first_name": "Вася",
          "pay_status": false,
          "last_name": "Пупкин",
          "username": "superVasssya",
          "profile_link": ""
        },
        {
          "id": 12,
          "email": "antonio@mail.com",
          "first_name": "Anton",
          "pay_status": true,
          "last_name": "Black",
          "username": "ABlack",
          "profile_link": "https://translate.google.com/"
        }
      ],
    };
  },
  mounted() {
    this.oldStaff = this.staff
  },
  components: {
    Controller,
    Table,
    Window,
    Search
  },
  methods: {
    search(val) {
      if (val === '') {
        this.staff = this.oldStaff;
        return
      }

      this.staff = this.oldStaff.filter((el) => {
        for (let key in el) {
          if (!(key === 'pay_status' || key === 'id')) {
            if (el[key].indexOf(val) !== -1) {
              return el
            }
          }
        }
      })
    },
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
    filter(filt) {
      if (filt === 'number') {
        this.staff = this.oldStaff;
        return;
      }

      this.staff = this.staff.sort((first, second) => {
        if (first[filt].toLowerCase() < second[filt].toLowerCase()) {
          return -1;
        }

        if (first[filt].toLowerCase() > second[filt].toLowerCase()) {
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
