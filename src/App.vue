<template>
  <TaskApp
    :completed-tasks="completedTasks"
    :tasks="tasks"
    @undelete-task="uncompleteTasks"
    @delete-task="deleteTask"
  />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TaskApp from './components/TaskApp.vue';

export default defineComponent({
  name: 'App',
  components: {
    TaskApp
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          text: 'Hello',
          day: 'May 4th'
        }
      ],
      completedTasks: [
        {
          id: 1,
          text: 'Hello',
          day: 'May 4th'
        }
      ]
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'eat',
        day: 'May 4th'
      },
      {
        id: 2,
        text: 'drive',
        day: 'May 4th'
      },
      {
        id: 3,
        text: 'Sleep',
        day: 'May 4th'
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

img {
  height: 30px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: green;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
