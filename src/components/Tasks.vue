<template>
    <div v-for="task in tasks" :key="task.id" class="my-1 space-y-3 px-7">
        <Task @delete-task = "$emit('delete-task', task.id)" :task = "task" @toggle-task = "$emit('toggle-task', task.id)"/>
    </div>
    
</template>

<script>

    import Task from './Task'
    export default {
        name: "Tasks",
        props: {
            tasks: Array
        },
        components: {
            Task
        },
        emits: ['delete-task', 'toggle-task']
    }
</script>
