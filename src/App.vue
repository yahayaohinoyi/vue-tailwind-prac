<template>
  <div class="flex justify-center">
    <div class="w-4/12 mt-10 border border-black rounded-md cursor-pointer">
      <Header :title="'Task Tracker'" @show-add-task="renderAddTask" :showAddTask="showAddTask"/>
      <div v-if="showAddTask">
        <AddTask @create-task="createTask"/>
      </div>
      <div class="mb-7">
        <Tasks @delete-task = "deleteTask" :tasks = "tasks" @toggle-task = "toggleTask"/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask"
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleTask(id) {
      this.tasks = this.tasks.map((task) => {
        return task.id == id ? {...task, reminder: !task.reminder} : task
      })
    },
    createTask(task) {
      this.tasks = [...this.tasks, task]
    },
    renderAddTask() {
      this.showAddTask = !this.showAddTask
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "School Appointment",
        day: "June 1st at 2:30 pm",
        reminder: false,
      },
      {
        id: 2,
        text: "Doctor Appointment",
        day: "December 1st at 9:30 pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Lawn Appointment",
        day: "May 1st at 2:00 pm",
        reminder: false,
      },
      {
        id: 4,
        text: "Cooking Appointment",
        day: "April 1st at 4:30 pm",
        reminder: true,
      },
    ];
  },
};
</script>
