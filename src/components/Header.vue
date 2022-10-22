<template>
  <header >
    <h1  >{{title}}</h1>
    <Button text="Save"  />
  </header>
</template>

<script>
import Button from "./Button.vue"  
import '../assets/tailwind.css'
export default {
  name: "Header",
  props: {
    title: String,
  },
  components: {
    Button
  }
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
