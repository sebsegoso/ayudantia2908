<template>
  <div>
    <h3>{{ titulo }}</h3>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.title }}
        <button @click="$emit('eliminar-tarea', task.id)">Eliminar</button>
      </li>
    </ul>
  </div>
</template>
  
  <script>
export default {
  props: {
    tasks: {
      type: Array,
      required: true
    },
    titulo: String
  }
}
</script>