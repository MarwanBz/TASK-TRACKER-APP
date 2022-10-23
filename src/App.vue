<template>
  <div class="container">
    <Header title="Task Tracker" @toggle-add-form="toggleShowForm" :showAddTask="showAddTask"/>
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";



export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks : [],
      showAddTask: false,
    }
  },
  methods: {
    toggleShowForm() {
      this.showAddTask = !this.showAddTask
    },

    addTask(task) {
      this.tasks.push(task)
      // this.tasks = [...this.tasks, task]
    },

    deleteTask(id) {
    this.tasks = this.tasks.filter((task) => task.id !== id)
  },

  toggleReminder(id){
    this.tasks = this.tasks.map((task)=> task.id === id ? {...task, reminder: !task.reminder } : task)
  },
  },

  created() {
    this.tasks =  [
      { id: 1, text: 'Reading 10 pages', day: 'October 24th 2022', reminder: true },
      { id: 2, text: 'Search for networking projects', day: 'October 25th 2022', reminder: true},
      { id: 3, text: 'finish vue course', day: 'October 28th 2022' , reminder: false},
      { id: 4, text: 'Feed the pretty cat', day: 'October 30th 2022', reminder: false}
    ]
  }
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
