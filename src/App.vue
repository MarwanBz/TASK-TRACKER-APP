<template>
  <div class="container">
    <Header title="Task Tracker" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

.container {
  max-width: 500px;
  min-height: 300px;
  margin: 30px auto;
  padding: 30px;
  overflow: auto;
  border: 1px solid crimson;
  border-radius: 5px;
}
</style>
