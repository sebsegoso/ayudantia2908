<template>
  <div>
    <h2>Contador de Clics</h2>
    <p>Número de clics: {{ counter }}</p>
    <button @click="incrementCounter">Haz clic aquí</button>
    <button @click="counter = 0">Reset</button>
    <hr />
    <div @dblclick="doSomething">Do something</div>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    incrementCounter() {
      this.counter++
    },
    doSomething() {
      alert('hiciste shift click')
    }
  }
}
</script>