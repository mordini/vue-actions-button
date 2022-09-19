<script setup>
import ToggleButton from './components/ToggleActionButton.vue';

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
