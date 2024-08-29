<template>
  <div>
    <h2>Lista de Tareas</h2>
    <ul>
      <li v-for="(task, index) in tasks" :key="task.id">
        {{ index + 1 }}. {{ task.title }}
        <button @click="removeTask(index)">Eliminar</button>
      </li>
    </ul>
    <p>{{ newTask }}</p>
    <input type="text" v-model="newTask" />
    <button @click="addTask">Agregar Tarea</button>
  </div>
</template>

<script>
export default {
  name: 'VFor',
  data() {
    return {
      tasks: [
        { id: 1, title: 'Estudiar Vue.js' },
        { id: 2, title: 'Desarrollar una aplicación' },
        { id: 3, title: 'Preparar la presentación' }
      ],
      newTask: ''
    }
  },
  methods: {
    addTask() {
      const newTask = { id: Date.now(), title: this.newTask }
      this.tasks.push(newTask)
      this.newTask = ''
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>