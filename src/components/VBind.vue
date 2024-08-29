<template>
  <div>
    <h2>Galería de Imágenes</h2>
    <img :src="imageUrl" :alt="imageDescription" />
    <button @click="changeImage">Cambiar Imagen</button>
  </div>
</template>
  
  <script>
export default {
  name: 'VBind',
  data() {
    return {
      imageUrl: 'https://thispersondoesnotexist.com/',
      imageDescription: 'Imagen de ejemplo'
    }
  },
  methods: {
    changeImage() {
      this.imageUrl = 'https://via.placeholder.com/200'
      this.imageDescription = 'Nueva imagen de ejemplo'
    }
  }
}
</script>