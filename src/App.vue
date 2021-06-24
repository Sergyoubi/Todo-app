<template>
  <div class="w-screen h-screen bg-gray-100 flex flex-col justify-center space-y-10">
    <p class="text-3xl text-gray-800 relative">Task App</p>
    <AddTask @addNewTask="getNewTask"/>
    <Task @deleteTask="removeTask" :tasks="tasks"/>
  </div>
</template>

<script>

import AddTask from './components/AddTask.vue'
import Task from './components/Task.vue'

export default {
  name: 'App',

  components: { AddTask, Task },

  data() {
    return {
      tasks: [
        { id: 1, title: 'Task 1', completed: false },
        { id: 2, title: 'Task 2', completed: false },
        { id: 3, title: 'Task 3', completed: false },
        { id: 4, title: 'Task 4', completed: false }
      ]
    }
  },

  methods: {
    getNewTask(data) {  //sended data from child component is accessed as a function argument
      this.tasks = [...this.tasks,data] //add new task to the tasks array(sended data ppty must match with data in parent component)
    },

    removeTask(id) {
      this.tasks = this.tasks.filter((task) => task.id != id )
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

}
</style>
