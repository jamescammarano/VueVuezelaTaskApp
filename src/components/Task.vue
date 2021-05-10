<template>
  <div class="task">
    <p>
      {{ text }}
      <button id="id" class="btn" @click="onDelete(task.id)">Complete</button>
    </p>
    {{ day }}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    id: {
      type: Number,
      default() {
        return 0;
      }
    },
    day: {
      type: String,
      default() {
        return 'Set Date';
      }
    },
    text: {
      type: String,
      default() {
        return 'Set Text';
      }
    }
  }
});
</script>

<style scoped>
.btn {
  float: right;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  width: 330px;
}
.task.reminder {
  border-left: 5px solid green;
}
.task:hover {
  background: #c2c1c1;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  width: 330px;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
