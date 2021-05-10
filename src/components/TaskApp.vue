<template>
  <div class="container">
    <div>
      <h1>VueVuezela Tasks</h1>
      <h3>To Do</h3>
      <ul v-for="task in tasks" :key="task.id">
        <Task :id="task.id" :day="task.day" :text="task.text" />
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
    <AddTask :on-click="onClick" />
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import AddTask from './AddTask.vue';
import Task from './Task.vue';

const TaskApp = defineComponent({
  name: 'TaskApp',
  components: {
    AddTask,
    Task
  },
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
            text: String,
            day: String
          }
        ];
      }
    }
  },
  emits: ['delete-task', 'undelete-task'],
  methods: {
    onClick(): void {
      console.log('click');
    },
    onDelete(id: number): void {
      this.$emit('delete-task', id);
    },
    onUncomplete(id: number): void {
      this.$emit('undelete-task', id);
    }
  }
});

export default TaskApp;
</script>
<style scoped lang="scss">
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
h1 {
  text-align: center;
}
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}
</style>
