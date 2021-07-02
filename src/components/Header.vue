<template>
  <div class="text-center">
      <div class="sm:flex mb-1 text-3xl sm:text-4xl sm:justify-between">
        <h1>{{title}}</h1>
        <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddtask ? 'Close' : 'Add Task'"/>
      </div>  
  </div>
</template>
    
<script>
import Button from './Button'
export default{
    name:'Header',
    props: {
        title: String,
        showAddTask: Boolean,
    },
    components: {
    Button,
  }
}
</script>

<style scoped>
    /* header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
} */
</style>
