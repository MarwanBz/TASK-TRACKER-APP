<template>
  
  <p v-show="tasks.length === 0" class="pt-12 pb-12">Nice You Completed All of Your Tasks For Today!🐱‍🏍🎂🎉</p>
    <div :key="task.id" v-for="task in tasks">
      <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />
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
  emits: ['delete-task', 'toggle-reminder'],
  
};
</script>

<style></style>
