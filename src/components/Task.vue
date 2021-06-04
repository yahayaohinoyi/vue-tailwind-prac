<template>
  <div
    @dblclick="toggleTask(task.id)"
    :class="[
      !task.reminder
        ? 'px-2 py-1 bg-gray-200 border-l-4 rounded-sm'
        : 'px-2 py-1 bg-gray-200 border-l-4 rounded-sm border-green-600'
    ]"
  >
    <h3 class="flex justify-between text-sm font-800">
      {{ task.text }}
      <i @click="onDelete(task.id)" class="text-red-500 fas fa-times"></i>
    </h3>
    <p class="text-sm font-light">
      {{ task.day }}
    </p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
    toggleTask(id) {
        this.$emit("toggle-task", id)
    },
  },
};
</script>
// "'px-2 py-1 bg-gray-200 border-l-4 rounded-sm'"
