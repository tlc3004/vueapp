<script setup lang="ts">
import { ref } from 'vue'
import CurvedCornerModal from './components/CurvedCornerModal.vue'

const mostrar = ref(false)
</script>

<template>
  <main>
    <h1>Compuerta Curva Inferior Izquierda 🚪</h1>
    <button @click="mostrar = !mostrar">
      {{ mostrar ? 'Cerrar' : 'Abrir' }} compuerta
    </button>

    <CurvedCornerModal :visible="mostrar">
      🚨 Acceso a los motores nucleares
    </CurvedCornerModal>
  </main>
</template>

<style scoped>
main {
  text-align: center;
  padding: 2rem;
}
button {
  padding: 10px 20px;
  background-color: #646cff;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}
</style>
