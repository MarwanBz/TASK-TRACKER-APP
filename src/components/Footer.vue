<template>
  <footer>
    <div class="container flex flex-col items-center justify-center">
        <p class="copyright text-slate-700">Copyright © 2022 All Rights Reserved</p>
        <p class="text-slate-700 pt-4 pb-4">App version 1.0</p>
        <router-link :v-bind="changePath" class="bg-sky-500 hover:bg-sky-700 text-xs text-white focus:outline-none focus:ring focus:ring-violet-300 pt-2 pb-2 pl-4 pr-4 rounded-lg" v-bind:to=url >{{text}}</router-link>
      </div>
  </footer>
</template>

<script>
export default {
  data(){
    return{
      url: './',
      text: 'About'
    }
  },
  computed: {
    changePath() {
      if(this.$route.path === this.url) {
        this.text = 'About'
        this.url = 'about'
      } else {
        this.text= 'Home'
        this.url = '/'
      }
    }
  }
};
</script>

<style>
.container {
  background-color: rgb(253, 52, 220);
  padding: 20px;
  overflow: auto;
  border-radius: 5px;
}

i {
  padding: 0 10px;
  font-size: 20px;
}
</style>
