<template>
  <div>
    <h4>Employee Details</h4>
    <div class="container">
      <div class="row">
        <div class="card" style="flex-wrap: wrap">
          <p>Name: {{ name }}</p>
          <p>Position: {{ position }}</p>
          <p>Department: {{ dept }}</p>
          <button class="btn btn-primary" @click="toggle()">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Employee",
  props: {
    name: String,
    position: String,
    dept: String,
    toggle: Function,
  },
};
</script>
<style>
.card {
  border: 2px solid black;
  width: 250px;
  height: auto;
  margin: 10px;
  padding: 10px;
  justify-content: center;
}
</style>
