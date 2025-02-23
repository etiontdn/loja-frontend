<template>
  <button class="burger-menu" @click="toggleMenu" :class="{ active: isActive }">
    <span class="line"></span>
    <span class="line"></span>
    <span class="line"></span>
  </button>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['toggle-menu'])
const isActive = ref(false)

function toggleMenu() {
    isActive.value = !isActive.value
    emit('toggle-menu')
}
</script>

<style scoped>
.burger-menu {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 2rem;
  height: 2rem;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  box-sizing: border-box;
}

.burger-menu:focus {
  outline: none;
}

.burger-menu.active .line:nth-child(1) {
  transform: rotate(45deg);
}

.burger-menu.active .line:nth-child(2) {
  opacity: 0;
}

.burger-menu.active .line:nth-child(3) {
  transform: rotate(-45deg);
}

.line {
  width: 2rem;
  height: 0.25rem;
  background-color: black;
  transition: all 0.3s linear;
  position: relative;
  transform-origin: 1px;
}
</style>