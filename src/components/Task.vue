<template>
    <div>
        <i @click="$emit('delete-task', task.id)" class="task transform fas fa-times p-1 hover:rotate-180 hover:text-red-600 hover:scale-110 transition delay-150 duration-300 ease-in-out rounded-full float-right cursor-pointer"></i>
        <h3 clas="">{{ task.text }}</h3>
        <div class="w-full h-1 bg-white my-1"></div>
        <i @dblclick="$emit('toggle-reminder', task.id)" class="transform fas fa-bell float-right p-1 cursor-pointer text-gray-400 hover:scale-110 hover:text-red-600 hover:relative hover:infinite-flex text-center animate-bounce transition delay-300 duration-30 ease-in-out"></i> 
        <p class="text-gray-600 text-xs">{{ task.day }}</p>      
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