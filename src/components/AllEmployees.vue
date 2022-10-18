<!-- eslint-disable prettier/prettier -->
<template>
  <!-- <div>
    <AddEmployee />
    <h1>All Employees</h1>
    <button>click</button>
    <div v-for="user in users" :key="user.name" style="display: flex">
      <div class="card">
        <p>Name: {{ user.name }}</p>
        <p>Position: {{ user.position }}</p>
        <p>Department: {{ user.dept }}</p>
        <button class="btn btn-primary">click</button>
      </div>
    </div>
  </div> -->

  <AddEmployee v-if="addUser" :toggle="toggleAdd" />


  <UpdateEmployee :eName="tempUser.name" :ePosition="tempUser.position" :eDept="tempUser.dept" v-if="updateUser"
    :toggle="toggleUpdate" :eId="tempUser._id"/>


  <br>

  <!-- <button @click="showDetalis=false" v-if="showDetalis">Hide</button> -->
  <Employee :name="tempUser.name" :position="tempUser.position" :dept="tempUser.dept" v-if="showDetalis"
    :toggle="toggleDetalis" />

  <h1>All Employees</h1>
  <h6 style="text-align: end;margin-right: 30px;"><a @click="toggleAdd()">+ Add Employee</a></h6>
  <div class="container">
    <div class="row">
      <div class="card" v-for="user in users" :key="user.name" style="flex-wrap: wrap">
        <p>Name: {{ user.name }}</p>
        <p>Position: {{ user.position }}</p>
        <p>Department: {{ user.dept }}</p>
        <div class="btn-group">
          <button class="btn btn-primary" @click="print(user)">Detais</button>
          <button class="btn btn-secondary" @click="updateDetais(user)">Update</button>
          <button class="btn btn-danger" @click="deleteEmployee(user._id)">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AddEmployee from "./AddEmployee.vue";
import UpdateEmployee from "./UpdateEmployee.vue";
import Employee from "./Employee.vue";

export default {
  name: "AllEmployees",
  data() {
    return {
      users: [],
      // eslint-disable-next-line no-undef
      tempUser: {},
      showDetalis: false,
      updateUser: false,
      addUser: false,
    };
  },
  async mounted() {
    let results = await axios.get("https://meanbackend.vercel.app/employees");
    this.users = results.data;
    // console.log(this.users[0]);
  },
  components: {
    AddEmployee,
    UpdateEmployee,
    Employee,
  },
  methods: {
    async deleteEmployee(abc) {
      console.log("deleted", abc);
      axios.delete("https://meanbackend.vercel.app/employees/" + abc);
      let results = await axios.get("https://meanbackend.vercel.app/employees");
      this.users = results.data;
    },
    print(abc) {
      this.tempUser = abc;
      // console.log(this.tempUser);
      this.toggleDetalis();
    },
    toggleDetalis() {
      this.showDetalis = !this.showDetalis;
    },
    updateDetais(abc) {
      console.log("updated");
      this.tempUser = abc;
      this.updateUser = true;
    },
    toggleUpdate() {
      this.updateUser = !this.updateUser;
    },
    toggleAdd() {
      this.addUser = !this.addUser;
      console.log("toggled");
    },
  },
};
</script>
<style>
.card {
  border: 2px solid black;
  width: 300px;
  height: auto;
  margin: 10px;
  padding: 10px;
  justify-content: center;
}
</style>
