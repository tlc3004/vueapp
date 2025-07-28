<script setup lang="ts">
import { ref } from 'vue'
import SlideModal from './components/SlideUpModal.vue'

type Direction = 'up' | 'down' | 'left' | 'right' | null
const modal = ref<Direction>(null)

function openModal(dir: Direction) {
  modal.value = dir
}

function closeModal() {
  modal.value = null
}
</script>

<template>
  <main>
    <h1>Modales Deslizantes</h1>
    <div class="botones">
      <button @click="openModal('up')">Desde Abajo</button>
      <button @click="openModal('down')">Desde Arriba</button>
      <button @click="openModal('left')">Desde la Derecha</button>
      <button @click="openModal('right')">Desde la Izquierda</button>
    </div>

    <SlideModal
      v-if="modal"
      :visible="true"
      :direction="modal"
      @close="closeModal"
    >
      <h2>Modal: {{ modal }}</h2>
      <p>Este modal entra desde {{ modal }}</p>
    </SlideModal>
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
  text-align: center;
}

.botones {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}

button {
  padding: 10px 20px;
  border: none;
  background-color: #646cff;
  color: white;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}
</style>
