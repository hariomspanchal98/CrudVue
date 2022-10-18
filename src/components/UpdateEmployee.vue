<template>
  <div>
    <h3>update- {{ eName }}</h3>
    <form class="card" style="width: 300px">
      <label>Name : </label>
      <input type="text" style="width: 100%" :value="eName" />
      <br />

      <label>Position:</label>
      <input type="text" style="width: 100%" :value="ePosition" />
      <br />

      <label>Department:</label>
      <input type="text" style="width: 100%" :value="eDept" />
      <br />

      <div class="btn-group">
        <button class="btn btn-primary" @click.prevent="updateUser()">
          Update
        </button>
        <button class="btn btn-secondary" @click="toggle()">Cancel</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UpdateEmployee",
  data() {
    return {
      user: {
        name: this.eName,
        position: this.ePosition,
        dept: this.eDept,
      },
    };
  },
  props: {
    eName: String,
    ePosition: String,
    eDept: String,
    eId: String,
    toggle: Function,
  },
  methods: {
    print() {
      console.log("abc");
    },
    async updateUser() {
      console.log(this.user);
      await axios.put(
        "https://meanbackend.vercel.app/employees/" + this.eId,
        this.user,
        (err) => {
          console.log(err);
        }
      );
    },
  },
};
</script>
