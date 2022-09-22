<!-- "I can do all things through him who strengthens me." -Philippians 4:13 -->
<template>
  <div class="centered">
    <button
      style="outline: none"
      @click="toggleActionState()"
      class="button"
      :class="[props.styles, reacts.colour]"
    >
      {{ reacts.currentLabel }}
    </button>
  </div>
</template>
<script setup>
console.log(`Loading ToggleButton component`);
import { reactive } from 'vue';
import '../assets/css/buttons/plastic.css';
import '../assets/css/buttons/cool.css';

// Define PROPS
const props = defineProps({
  // Get action labels
  labels: Array,
  // Get actions to perform
  actions: Array,
  colour: Array,
  styles: String,
});

// Define emits
const emit = defineEmits(['doAction']);

// Make reactive vars
const reacts = reactive({
  currentLabel: props.labels[0],
  action: props.actions[0],
  colour: props.colour[0],
});

// Set initital action states
let actionState = false;

// Change label and action, send action to parent
function toggleActionState() {
  // Send action to parent
  emit('doAction', reacts.action);

  // Toggle between action states for next click
  if (!actionState) {
    reacts.currentLabel = props.labels[1];
    reacts.action = props.actions[1];
    reacts.colour = props.colour[1];
  } else {
    reacts.currentLabel = props.labels[0];
    reacts.action = props.actions[0];
    reacts.colour = props.colour[0];
  }

  // Change state to opposite of previous
  actionState = !actionState;
}
</script>

<style scoped></style>
