<template>
  <form @submit.prevent="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task: </label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time: </label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder: </label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input
      type="submit"
      value="Save Task"
      class="bg-sky-500 hover:bg-sky-700 text-xs text-white focus:outline-none focus:ring focus:ring-violet-300 pt-2 pb-2 pl-4 pr-4 rounded-xl w-full cursor-pointer"
    />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },

  methods: {
    onSubmit() {
      if (!this.text) {
        alert("please add a task");
        return;
      }
      const newTask = {
        // id: Math.floor(Math.random() * 1000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.$emit('add-task', newTask)
      this.text = "";
      this.day = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
  color: #6f7e94;
  font-weight: bold;
}
.form-control input {
  border-radius: 5px;
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
  outline-color: skyblue;
  border-bottom: 1px;
  border-bottom-color: skyblue;
  border-bottom-style: solid;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
