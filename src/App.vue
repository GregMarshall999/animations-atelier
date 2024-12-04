<template>
  <nav>
    <RouterLink to="/">Home</RouterLink> |
    <RouterLink :to="{ name: 'About' }">About</RouterLink> |
    <RouterLink :to="{ name: 'Contact' }">Contact</RouterLink>
  </nav>
  <RouterView v-slot="{ Component }">
    <Transition name="route" mode="out-in">
      <component :is="Component"></component>
    </Transition>
  </RouterView>
</template>

<script setup>
import { RouterView } from 'vue-router'
</script>

<style>

body {
  font-family: Avenir, Hevletica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  background: #f2f2f2;
}

.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
.route-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}
.route-enter-active {
  transition: all 0.3s ease-out;
} 
.route-leave-active {
  transition: all 0.3s ease-in;
}
</style>
