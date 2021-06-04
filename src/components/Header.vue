<template>
  <div class="flex justify-between p-7">
    <h3 class="font-serif text-lg font-bold">
      {{ title }}
    </h3>
    <Button
      :showAddTask="showAddTask"
      @click-add-btn="renderAddTask"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </div>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  methods: {
    renderAddTask() {
      this.$emit("show-add-task");
    },
  },
};
</script>
