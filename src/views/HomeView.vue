<template>
  <div class="home">
    <AllEmployees />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import AllEmployees from "../components/AllEmployees.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
    AllEmployees,
  },
};
</script>
