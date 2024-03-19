<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.datetime.replace("T", " at ") }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object,
  },
}
</script>

<style scope>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  color: green;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  color: red;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
