<template>
  <div class="container flex justify-items-center justify-center align-items-center overflow-auto font-mono">
    <div class="box-border m-7 sm:m-14 md:m-24 p-4 sm:p-8 border-2 border-yellow-200 ring-1 rounded  w-full sm:w-3/4 md:2/4 max-w-lg z-10 bg-gradient-to-r from-yellow-300">
      <div class="font-semibold" >
        <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask"/>
      <div>
        <div class="block m-0 p-0" v-show="showAddTask">
            <AddTask @add-task="addTask"/>
        </div>
      </div> 
    </div>
      <div class="py-8">
        <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },

  data () {
    return{
      tasks:[],
      showAddTask: false,
    } 
  },
  methods: {
    addTask(task) {
      this.tasks=[...this.tasks, task]
    },
    toggleAddTask(){
        this.showAddTask=!this.showAddTask
    },
    deleteTask(id) {
      if (confirm('Are you realy want to delete this task ?')) {
        this.tasks= this.tasks.filter((task)=>task.id!==id)
      }  
    },
    toggleReminder (id) {
      if (confirm('Set or Unset remionder!')) {
          this.tasks=this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
      }
    
    }
  },
 

  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 5th at 2.30pm',
        reminder: true,

      },
      {
        id: 2,
        text: 'Shoping for ramadan',
        day: 'April 10th at 4.30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Training with Brad',
        day: 'April 12th at 4.30pm',
        reminder: false,
      },
    ]
  }
}
</script>
