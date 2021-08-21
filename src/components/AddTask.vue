<template>
      <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input class="taskInput" type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        class="taskInput"
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input  type='checkbox' value="boolean" class="m-auto" v-model="reminder" data-on-color:bg-yellow-600 name="reminder">
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

