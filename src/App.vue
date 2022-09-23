<script setup>
import { reactive } from 'vue';
import ActionsButton from './components/ActionsButton.vue';

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
</script>

<!-- This is how you use the component in your app's template -->
<template>
  <div>{{ reacts.clicked }}</div>
  <ActionsButton
    @doAction="this[$event]()"
    styles="large"
    :labels="['Start', 'Stop']"
    :actions="['start', 'stop']"
    :colour="['green', 'red']"
  />
</template>

<style scoped></style>
