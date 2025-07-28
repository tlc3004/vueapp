<script setup lang="ts">
import { ref } from 'vue'
import SlideUpModal from './components/SlideUpModal.vue'

const modal = ref<null | 'up'>(null)
</script>

<template>
  <main>
    <h1>Modales</h1>
    <button @click="modal = 'up'">Desde abajo</button>

    <SlideUpModal :visible="modal === 'up'" @close="modal = null">
      <h2>Slide Up</h2>
    </SlideUpModal>
  </main>
</template>

<style scoped>
main {
  text-align: center;
  padding: 2rem;
}
button {
  margin: 0.5rem;
  padding: 10px 20px;
  background: #646cff;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
</style>
