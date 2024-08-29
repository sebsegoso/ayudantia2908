<script>
export default {
  props: ['sections'],
  data() {
    return {
      selectedSection: 0
    }
  }
}
</script>

<template>
  <div class="presenta-diapos">
    <nav>
      <button
        :class="{ active: idx === selectedSection }"
        v-for="(section, idx) in sections"
        :key="idx"
        @click="selectedSection = idx"
      >
        {{ section.buttonText }}
      </button>
    </nav>

    <main>
      <component :is="sections[selectedSection].component" />
    </main>
  </div>
</template>

<style scoped>
.presenta-diapos {
  display: flex;
  flex-direction: column;
  height: 100vh;
  background: #fafafa;
}
nav {
  background-color: aliceblue;
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 1rem;
  box-shadow: 1px 0 10px #777;
}

nav button {
  padding: 0.5rem;
  background-color: #42b88380;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.5s;
}

nav button.active {
  background-color: #42b883;
  scale: 1.1;
}
main {
  padding: 3rem;
  flex-grow: 1;
  overflow: auto;
}
</style>