<template>
  <div class="mx-auto bg-gray-100 mt-10">
    <p class="flex justify-between items-center">
      <input type="checkbox" :checked="task.completed" @change="markComplete">

      <span class="mr-96" :class="{ 'is-complete' :task.completed }">{{ task.title }}</span> <!-- dynamic class is applyed if condition is TRue -->

      <button @click="$emit( 'deleteTask', task.id )" class="bg-blue-400 p-1 px-2 rounded-lg hover:bg-blue-500 focus:outline-none">Delete</button>

      <button @click="update" class="bg-red-300 p-1 px-2 rounded-lg hover:bg-red-400 focus:outline-none">Update</button>
    </p>

    <div id="updateFormcontainer" v-if="this.flag" class="mt-5">
      <form @submit="updateTask">
        <div class="w-full h-full flex justify-evenly">
          <input type="text" placeholder="Type here" v-model="updateTitle" class="w-6/12 border-2 border-gray-400 focus:outline-none">
          <input type="submit" name="button" value="Update Task" class="rounded-xl w-1/5 bg-gray-400 text-gray-800 hover:bg-gray-500">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ['task', 'tasks'],

  data() {
    return {
      flag: false,
      updateTitle: ''
    }
  },

  methods: {
    markComplete() {
      this.task.completed = !this.task.completed
    },
    update() {
      this.flag = !this.flag
    },
    updateTask(e) {
      e.preventDefault()
      this.tasks.filter((task) => {
        if ( task.id === this.task.id ) {
          //update a task's title
          task.title = this.updateTitle
        }
        //reset flag's value
        this.flag = false
      })
    }
  }
}
</script>

<style>
  .is-complete {
    text-decoration: line-through;
  }
</style>

<!-- on btn click, fire a custom event and send 'task.id' as a Payload to App.vue, but first of all we send it to Task.vue 
     because TaskItem.vue is a child component of Task.vue. TaskItem.vue -> Task.vue –App.vue
-->

