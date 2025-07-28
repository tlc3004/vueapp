<template>
  <transition name="slide-up">
    <div v-if="visible" class="overlay" @click.self="emit('close')">
      <div class="modal">
        <slot />
      </div>
    </div>
  </transition>
</template>

<script setup lang="ts">
defineProps<{
  visible: boolean
}>()

const emit = defineEmits(['close'])
</script>

<style scoped>
.overlay {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: flex-end;
  justify-content: center;
  z-index: 1000;
}
.modal {
  background: white;
  padding: 2rem;
  border-radius: 1rem 1rem 0 0;
  width: 90%;
  max-width: 500px;
}
.slide-up-enter-active,
.slide-up-leave-active {
  transition: transform 0.3s ease;
}
.slide-up-enter-from,
.slide-up-leave-to {
  transform: translateY(100%);
}
</style>
