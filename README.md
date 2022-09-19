# Vue 3 Toggle Button

Toggle State on-off, because I got tired of re-making it for various little things.

## Using

I'll fill this out later. this example is good enough for now.
Besides, I'm the only one using it right now :D

## How To Use

```
<!-- Import the button -->
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
<!-- For now, only two events are allowed -->
  <ToggleButton
    @doAction="this[$event]()"
    :labels="['Play', 'Stop']"
    :actions="['playAudio', 'stopAudio']"
  />
</template>

<style scoped></style>
```
