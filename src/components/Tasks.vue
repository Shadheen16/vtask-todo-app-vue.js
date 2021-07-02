<template>
    <div :key="task.id" v-for="task in tasks" class="my-2 bg-gradient-to-r from-white p-2 rounded shadow-md">
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)"  @delete-task="$emit('delete-task', task.id)" :task='task'/>
    </div>
</template>

<script>
import Task from './Task'
export default{
    name: 'Tasks',
    props: {
        tasks: Array,
    },
    components: { 
       Task,
    },
emits: ["delete-task", "toggle-reminder"],
}
</script>
