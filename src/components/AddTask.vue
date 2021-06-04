<template>
  <div class="mb-6 space-y-3 px-7">
    <form @submit="saveTask" class="space-y-4">
      <div>
        <label for="task" class="text-sm"> Task </label><br />
        <input
          name="add-task"
          type="text"
          id="add-task"
          placeholder="Add Task"
          class="w-4/6 pl-2 border border-black rounded-md h-9"
          v-model="text"
        />
      </div>

      <div>
        <label for="day" class="text-sm"> Day & Time </label><br />
        <input
          name="add-task"
          type="text"
          id="add-task"
          placeholder="Add Day & time"
          class="w-4/6 pl-2 border border-black rounded-md h-9"
          v-model="day"
        />
      </div>

      <div class="flex justify-between">
        <label class="text-sm"> Set Reminder </label><br />
        <input type="checkbox" v-model="reminder" />
      </div>

     <div class="flex justify-center">
        <button class="w-4/5 h-10 text-sm text-white bg-black rounded-md" @click="saveTask">
            Save Task
        </button>
     </div>


    </form>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
      return {
          id: "",
          text: "",
          day: "",
          reminder: false
      }
  },
  methods: {
      saveTask(e) {
          e.preventDefault()
          this.$emit('create-task', {id: Math.floor(Math.random() * 100000), text: this.text, day: this.day, reminder: this.reminder})
          this.clearform()
      },
      clearform() {
          this.id = "",
          this.task = "",
          this.day = "",
          this.reminder = false
      }
  }
};
</script>
