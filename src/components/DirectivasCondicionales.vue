<template>
  <div>
    <h2>Bienvenido</h2>
    <p v-if="isLoggedIn">Bienvenido de nuevo, {{ username }}.</p>
    <p v-else-if="isGuest">Bienvenido, invitado.</p>
    <p v-else>Por favor, inicia sesión para continuar.</p>

    <button @click="toggleLogin">
      {{ isLoggedIn || isGuest ? 'Cerrar Sesión' : 'Iniciar Sesión' }}
    </button>
    <button v-if="!isGuest" @click="isGuest = true">Entrar como invitado</button>
  </div>
</template>

<script>
export default {
  name: 'DirectivasCondicionales',
  data() {
    return {
      username: 'Pepito',
      isLoggedIn: false,
      isGuest: false
    }
  },
  methods: {
    toggleLogin() {
      const isLoggedInOrGuest = this.isLoggedIn || this.isGuest
      this.isLoggedIn = !isLoggedInOrGuest
      this.isGuest = !isLoggedInOrGuest
    }
  }
}
</script>