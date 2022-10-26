<template>
  <button v-show="homePage" @click="$emit('toggle-form')" :style="{ background: color }" class="bg-sky-500 hover:bg-sky-700 text-xs text-white focus:outline-none focus:ring focus:ring-violet-300 pt-2 pb-2 pl-4 pr-4 rounded-xl">{{text}}</button>
  
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String,
  },
  computed: {
    homePage() {
      if(this.$route.path === '/') {
        return true
      } else {
        return false
      }
    }
  }
}
</script>

<style> 

</style>