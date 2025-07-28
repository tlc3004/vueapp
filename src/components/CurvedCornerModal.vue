<template>
  <div class="corner-wrapper">
    <div class="quarter-circle" :class="{ open: visible }">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{ visible: boolean }>()
</script>

<style scoped>
.corner-wrapper {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 300px; /* Más grande */
  height: 300px; /* Más grande */
  perspective: 1200px;
  pointer-events: none;
  z-index: 999;
}

.quarter-circle {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle at bottom left, #5c5fff, #2a2a88);
  border-radius: 0 100% 0 0;
  transform-origin: bottom left;
  transform: rotateZ(90deg);
  transition: transform 0.7s ease-in-out;
  pointer-events: auto;
  display: flex;
  align-items: flex-end;
  justify-content: flex-start;
  color: white;
  font-weight: bold;
  padding: 1.5rem;
  box-shadow: 0 -8px 24px rgba(0, 0, 0, 0.6);
  overflow: hidden;
}

.quarter-circle.open {
  transform: rotateZ(0deg);
}
</style>
