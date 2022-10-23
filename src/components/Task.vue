<template>
  <div @dblclick="$emit('toggle-reminder', task.id)"
      :class="[task.reminder ? 'reminder' : '', 'task' ]">
    <h3>{{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fa fa-times-circle"></i></h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
};
</script>

<style scoped>

  .fa {
    color: red;
  }
  .task {
    background: #dfdfdf;
    padding: 10px 20px;
    cursor: pointer;
    margin: 5px;
  }
  .task.reminder {
    border-left: 5px solid skyblue;
  }

  .task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>
