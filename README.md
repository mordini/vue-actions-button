# Vue 3 Toggle Button

Toggle State on-off, because I got tired of re-making it for various little things.

## How To Use

You can just clone the whole repository from here and run

```
npm install
npm run dev
```

to see how it goes.

I'll fill this out later. this example is good enough for now.
Besides, I'm the only one using it right now :D

```
<script setup>
// Import the button
import { reactive } from 'vue';

// for the local testing, after installing from the npm registry you want to use @mordini
// import ToggleButton from './components/ToggleButton.vue';

import ToggleButton from '@mordini/vue-toggle-button';

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
  <ToggleButton
    @doAction="this[$event]()"
    styles="large"
    :labels="['Start', 'Stop']"
    :actions="['start', 'stop']"
    :colour="['green', 'red']"
  />
</template>

<style scoped></style>
```
