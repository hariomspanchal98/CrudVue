<template>
  <div>
    <h1>HelloWorld component</h1>
    <h4>{{ msg }}</h4>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
};
</script>
