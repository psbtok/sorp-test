<script setup lang="ts">
import NavigationComponent from './components/NavigationComponent.vue'; 
import { RouterView } from 'vue-router';
</script>

<style>
main {
  width: 100vw;
  height: 100dvh;
  display: flex;
  flex-direction: column;
}
</style>

<template>
  <main>
    <NavigationComponent />
    <RouterView />
  </main>
</template>

<style scoped>
</style>
