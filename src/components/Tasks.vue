<template>
  <div>
    <div  v-for="i in tasks">
        <h3 >{{ i.text }}</h3>
      <!-- <Task :task="task" /> -->
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
};
</script>

<style></style>
