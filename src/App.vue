<script setup>
import { reactive } from 'vue';
import ToggleButton from './components/ToggleButton.vue';

const reacts = reactive({
  clicked: 'Not Clicked',
});

// Declare functions to toggle between
function start() {
  reacts.clicked = 'Start Clicked!';
}
function stop() {
  reacts.clicked = 'Stop Clicked!';
}

// make it so button can be red or green depending on stop/start
</script>

<!-- This is how you use the component in your app's template -->
<template>
  <div>{{ reacts.clicked }}</div>
  <ToggleButton
    @doAction="this[$event]()"
    styles="large"
    :labels="['Start', 'Stop']"
    :actions="['start', 'stop']"
    :colour="['green', 'red']"
  />
</template>

<style scoped></style>
