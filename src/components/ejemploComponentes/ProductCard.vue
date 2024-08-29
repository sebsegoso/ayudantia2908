
<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <slot name="content">
      <!-- aqui -->
    </slot>
    <hr />
    <slot name="action"> </slot>
  </div>
</template>

<script>
export default {
  props: ['title']
}
</script>

<style scoped>
.card {
  background: yellow;
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>