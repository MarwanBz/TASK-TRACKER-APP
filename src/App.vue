<template>
  <div class="app-container">
    <Header
      title="Task Tracker App"
      @toggle-add-form="toggleShowForm"
      :showAddTask="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      showAddTask: false,
    };
  },
  methods: {
    toggleShowForm() {
      this.showAddTask = !this.showAddTask;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #64748B;
}

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  min-height: 100vh;
  background-image: linear-gradient(#ffdce3, #ffcaff);
  background-repeat: no-repeat;
}

.app-container {
  background-image: linear-gradient(#ff8ea5, #ff68ff);
  max-width: 500px;
  min-height: 300px;
  margin: 30px auto;
  padding: 30px;
  overflow: auto;
  border-radius: 5px;
  box-shadow: 1px 3px 15px rgb(114 114 114 / 47%);
}

h3 {
  font-size: 18px;
  font-weight: bolder;
}
</style>
