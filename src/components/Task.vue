<template>
  <div class="w-7/12 mx-auto">
    <div v-for="task in tasks" :key="task.id">
      <TaskItem @deleteTask="$emit( 'deleteTask', task.id )" :task="task" :tasks="tasks"/>  <!--Each task is sended to TaskItem.vue as a prop! each task is now a single components--> <!-- second tasks is for updating each tasks -->
    </div>
  </div> 
</template>

<script>
import TaskItem from './TaskItem.vue'
export default {
  props: ['tasks'],
  components: { TaskItem }
}
</script>
