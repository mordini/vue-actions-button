<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { onMounted } from 'vue';
import ToggleButton from './components/ToggleActionButton.vue';

onMounted(() => {
  console.log('mounted');
});

// Declare functions to toggle between
function playAudio() {
  console.log(`SUCCESS playAudio`);
}
function stopAudio() {
  console.log(`SUCCESS stopAudio`);
}
</script>

<template>
  <ToggleButton
    @doAction="this[$event]()"
    :labels="['Play', 'Stop']"
    :actions="['playAudio', 'stopAudio']"
  />
</template>

<style scoped></style>
