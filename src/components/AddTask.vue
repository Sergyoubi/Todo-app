<template>
  <div class="w-9/12 h-10 mx-auto">
    <form @submit="addTask">
      <div class="w-full h-full flex justify-evenly">
        <input type="text" v-model="task" placeholder="Type a new Task" required class="w-6/12 border-2 border-gray-400 focus:outline-none pl-4">
        <input type="submit" name="button" value="Add Task" class="rounded-xl w-1/5 bg-green-200 text-gray-800 hover:bg-green-300">
      </div>
    </form>
  </div>
</template>

<script>
export default {

  data() {
    return {
      task: '',
    }
  },

  methods: {

    addTask(e) {

      e.preventDefault()

      const newtasks = { id: Date.now(), title: this.task, completed: false }
      
      //Send newTask(as data, aka: payloads) to App.vue and insert newTask to the task array there 
      this.$emit("addNewTask", newtasks)

      this.task = '' //reconvert this.task as an empty string again

    }
  }

}
</script>

<style scoped>
  
</style>