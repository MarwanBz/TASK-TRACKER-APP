<template>
  <header >
    <h1  >{{title}}</h1>
    <Button :color="showAddTask? 'red': '' " :text="showAddTask ? 'Close' : 'Add Task'"  @toggle-form="$emit('toggle-add-form')" />
  </header>
</template>

<script>
import Button from "./Button.vue"  
import '../assets/tailwind.css'
export default {
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    Button
  },
};
</script>

<style scoped>

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
