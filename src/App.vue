<template>
  <div class="container">
    <Header
      title="Task Tracker"
      @toggle-add-form="toggleShowForm"
      :showAddTask="showAddTask"
    />
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
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    toggleShowForm() {
      this.showAddTask = !this.showAddTask;
    },

    async addTask(task) {
      console.log(task);
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },

    async deleteTask(id) {
      const res = await fetch(`api/tasks/${id}`, {
        method: "DELETE",
      });
      res.status === 200
        ? (this.tasks = this.tasks.filter((task) => task.id !== id))
        : alert("Error deleting task");
    },

    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updTask ={...taskToToggle, reminder :!taskToToggle.reminder}

      const res = await fetch(`api/tasks/${id}`,{
        method: 'PUT',
        headers: {
          'Content-type' : 'application/json',
        },
        body: JSON.stringify(updTask)
      })
      const data = await res.json()
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },

    async fetchTasks() {
      const res = await fetch("api/tasks");
      const data = await res.json();
      return data;
    },

    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },

  async created() {
    this.tasks = await this.fetchTasks();
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
