<template>
  <div class="text-center">
      <div class="sm:flex mb-1 text-3xl sm:text-4xl sm:justify-between">
        <h1>{{title}}</h1>
        <Button @click="showAddtask()" v-show="!show" @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"  />
        <Button @click="showAddtask()" v-show="show" @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'"/>
      </div>  
  </div>
</template>
    
<script>
import Button from './Button'
export default{
  data() {
    return{
       show: false
    }
   
  },
    name:'Header',
    props: {
        title: String,
        showAddTask: Boolean,
    },
    components: {
    Button,
  },
  methods: {
    showAddtask(){
      this.show = !this.show
    }
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
