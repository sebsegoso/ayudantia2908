<template>
  <form @submit.prevent="submitTask">
    <input v-model="newTaskTitle" placeholder="Nueva tarea" />
    <button type="submit">Agregar Tarea</button>
  </form>
</template>
  
  <script>
export default {
  data() {
    return {
      newTaskTitle: ''
    }
  },
  methods: {
    submitTask() {
      if (this.newTaskTitle.trim()) {
        /* valida que haya algo de texto */
        this.$emit('agregar-tarea', { id: new Date().getTime(), title: this.newTaskTitle })
        this.newTaskTitle = '' /* resetea input */
      }
    }
  }
}
</script>