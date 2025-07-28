<template>
  <transition :name="transitionName">
    <div v-if="visible" class="overlay" @click.self="handleClose">
      <div class="modal" :class="direction">
        <slot />
      </div>
    </div>
  </transition>
</template>

<script setup lang="ts">
const props = defineProps<{
  visible: boolean
  direction: 'up' | 'down' | 'left' | 'right'
}>()

const emit = defineEmits<{ (e: 'close'): void }>()

function handleClose() {
  emit('close')
}

const transitionName = `slide-${props.direction}`
</script>

<style scoped>
.overlay {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  width: 90%;
  max-width: 400px;
  transition: transform 0.3s ease;
}

/* Dirección de entrada personalizada */
.slide-up-enter-from,
.slide-up-leave-to {
  transform: translateY(100%);
}
.slide-up-enter-active,
.slide-up-leave-active {
  transition: transform 0.3s ease;
}

.slide-down-enter-from,
.slide-down-leave-to {
  transform: translateY(-100%);
}
.slide-down-enter-active,
.slide-down-leave-active {
  transition: transform 0.3s ease;
}

.slide-left-enter-from,
.slide-left-leave-to {
  transform: translateX(100%);
}
.slide-left-enter-active,
.slide-left-leave-active {
  transition: transform 0.3s ease;
}

.slide-right-enter-from,
.slide-right-leave-to {
  transform: translateX(-100%);
}
.slide-right-enter-active,
.slide-right-leave-active {
  transition: transform 0.3s ease;
}
</style>
