<template>
  <div class="navigation">
    <button @click="goBack">
      <img src="../assets/arrow-left.svg" alt="Back" class="icon" />
      Back
    </button>
    <h1>{{ currentComponentName }}</h1>
  </div>
</template>

<style scoped>
.navigation {
  margin-top: 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

button {
  padding: 12px 16px;
  font-size: 16px;
  cursor: pointer;
  position: absolute;
  background: none;
  font-weight: 700;
  color: var(--highlight-purple);
}

.icon {
  width: 1em; 
  height: 1em;
  margin-right: 3px;
  position: relative;
  top: 2px;
}

h1 {
  margin: 0;
  font-size: 24px;
  flex-grow: 1;
  text-align: center;
  text-transform: capitalize;
}
</style>

<script setup lang="ts">
import { useRouter, useRoute } from 'vue-router';
import { ref, watch } from 'vue';

const router = useRouter();
const route = useRoute();

const currentComponentName = ref('');

// Watch for route changes to update the component name
watch(route, (newRoute) => {
  currentComponentName.value = newRoute.name || 'Home'; // Default to 'Home' if no name
});

// Method to go back to the previous route
const goBack = () => {
  router.back();
};
</script>
