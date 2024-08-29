<template>
  <section>
    <h2>Tarjetas de Producto</h2>
    <ProductCard title="SHAMPOO">
      <template #action> <button @click="purchaseProduct">Comprar</button></template>
      <template #content>
        <p>hola</p>
      </template>
    </ProductCard>
    <ProductCard title="JABÓN">
      <template #content>
        <p>
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Doloribus sit amet assumenda ea
          unde, voluptas officiis! Quis quidem maiores temporibus. Numquam in harum laboriosam,
          obcaecati ut natus placeat illo? Voluptatibus?
        </p>
      </template>
    </ProductCard>
  </section>
</template>
  
  <script>
import ProductCard from './ProductCard.vue'

export default {
  components: {
    ProductCard
  },
  methods: {
    purchaseProduct() {
      alert('Producto comprado!')
    }
  }
}
</script>
<style scoped>
section {
  background-color: #f00;
}
</style>