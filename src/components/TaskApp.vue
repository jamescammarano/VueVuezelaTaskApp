<template>
  <div>
    <div>
      <h1>VueVuezela Tasks</h1>
      <h3>To Do</h3>
      <ul v-for="task in tasks" :key="task.id">
        <li>{{ task.text }} <button id="task.id" @click="onDelete(task.id)">Complete</button></li>
      </ul>
    </div>
    <div>
      <h3>Completed Tasks</h3>
      <ul v-for="task in completedTasks" :key="task.id">
        <li>
          {{ task.text }}
          <img alt="vuvuzela" src="../assets/vuvuzela.png" @click="onUncomplete(task.id)" />
        </li>
      </ul>
    </div>
    <button @click="onClick">Add Task</button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

const TaskApp = defineComponent({
  name: "TaskApp",
  props: {
    tasks: {
      type: Array,
      default(): Array<Record<string, unknown>> {
        return [
          {
            id: Number,
            text: String
          }
        ];
      }
    },
    completedTasks: {
      type: Array,
      default(): Array<Record<string, unknown>> {
        return [
          {
            id: Number,
            text: String
          }
        ];
      }
    }
  },
  emits: ["delete-task", "undelete-task"],
  methods: {
    onClick(): void {
      console.log("click");
    },
    onDelete(id: number): void {
      this.$emit("delete-task", id);
    },
    onUncomplete(id: number): void {
      this.$emit("undelete-task", id);
    }
  }
});

export default TaskApp;
</script>
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}
img {
  height: 30px;
}
</style>
