<template>
  <div>
    <h2>Add New Employee</h2>
    <form class="card" style="width: 300px">
      <label>Name : </label>
      <input type="text" style="width: 100%" v-model="formValue.name" />
      <br />

      <label>Position:</label>
      <input type="text" style="width: 100%" v-model="formValue.position" />
      <br />

      <label>Department:</label>
      <input type="text" style="width: 100%" v-model="formValue.dept" />
      <br />

      <div class="btn-group">
        <button class="btn btn-primary" type="button" @click="addEmployee()">
          Submit
        </button>
        <button
          class="btn btn-secondary"
          type="button"
          @click.prevent="toggle()"
        >
          Cancel
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AddEmployee",
  data() {
    return {
      formValue: {
        name: "",
        position: "",
        dept: "",
      },
    };
  },
  props: {
    toggle: Function,
  },
  methods: {
    print() {
      console.log(this.formValue.name);
      console.log(this.formValue.position);
      console.log(this.formValue.dept);
      console.log("submitted");
    },
    async addEmployee() {
      console.log(this.formValue);
      await axios.post(
        "https://meanbackend.vercel.app/employees",
        this.formValue
      );
    },
  },
};
</script>
