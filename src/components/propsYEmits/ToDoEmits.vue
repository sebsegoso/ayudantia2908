<template>
  <div>
    <button @click="tasks = []">Limpiar tareas</button>
    <h2>Lista de Tareas</h2>
    <TaskForm @agregar-tarea="addTask" />
    <TaskList titulo="Mis tareas" :tasks="tasks" @eliminar-tarea="removeTask" />
  </div>
</template>
  
<script>
import TaskForm from './TaskForm.vue'
import TaskList from './TaskList.vue'
export default {
  components: {
    TaskForm,
    TaskList
  },
  data() {
    return {
      tasks: [
        { id: 1, title: 'Estudiar Vue.js' },
        { id: 2, title: 'Desarrollar una aplicación' }
      ]
    }
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask)
    },
    removeTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    }
  }
}
</script>