<template>
  <TaskApp
    :completed-tasks="completedTasks"
    :tasks="tasks"
    @undelete-task="uncompleteTasks"
    @delete-task="deleteTask"
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TaskApp from "./components/TaskApp.vue";

export default defineComponent({
  name: "App",
  components: {
    TaskApp
  },
  data() {
    return {
      tasks: [{ id: 1, text: "Hello" }],
      completedTasks: [{ id: 1, text: "Hello" }]
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "eat"
      },
      {
        id: 2,
        text: "drive"
      },
      {
        id: 3,
        text: "Sleep"
      }
    ];
  },
  methods: {
    deleteTask(id: number) {
      this.completedTasks.push(this.tasks.filter(task => task.id === id)[0]);
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    uncompleteTasks(id: number) {
      this.tasks.push(this.completedTasks.filter(task => task.id === id)[0]);
      this.completedTasks = this.completedTasks.filter(task => task.id !== id);
    }
  }
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
