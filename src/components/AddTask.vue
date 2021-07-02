<template>
      <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input  type='checkbox' value="boolean" class="transform " v-model="reminder" data-on-color:bg-yellow-600 name="reminder">
    </div>

    <input type="submit" value="Save Task" class="w-full transform bg-black bg-opacity-60 hover:scale-95 hover:bg-yellow-600 delay-300 duration-300 ease-in-out mt-4 py-1 md:py-2 rounded   text-white cursor-pointer"/>
  </form>
</template>

<script>
    export default {
        name: 'AddTask',
        props: {
          
         },
        data() {
          return  {
            text: "",
             day: "",
        reminder: false
          } 
        },
        methods: {
          onSubmit(e){
            e.preventDefault();
            if(!this.text){
              alert('Please add a task');
              return
            }
            const newTask={
              id: Math.floor(Math.random() * 100000),
              text: this.text,
              day: this.day,
              reminder: this.reminder
            }
            this.$emit('add-task', newTask);

            this.text="";
            this.day="";
            this.reminder=false
          }
      }
    }
</script>

<style scoped>
  
  .label { 
    @apply inline-block 
 }

 .add-form {
    @apply mb-0
  }
  .form-control {
    @apply my-2
  }
  .form-control label {
    @apply block
  } 
  .form-control input {
    @apply w-full h-7 sm:h-10 transform delay-75 mt-1 px-2 py-3 rounded bg-white bg-opacity-50 shadow border-yellow-900 hover:scale-105 cursor-pointer transition delay-150 duration-300 ease-in-out
  }
  .form-control-check {
    @apply flex mt-4 ml-1 justify-items-center justify-between
  } 
  .form-control-check label {
  @apply flex-1 
  }
  .form-control-check input{
   @apply p-0 shadow-none border-none  transform transition delay-150 duration-300 ease-in-out hover:text-yellow-600  text-white cursor-pointer rounded text-xl flex-1 focus-within:text-yellow-600
  } 
</style>
