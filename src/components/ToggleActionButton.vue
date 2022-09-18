<template>
  <div>
    <button @click="toggleActionState()">
      {{ reacts.currentLabel }}
    </button>
  </div>
</template>
<script setup>
console.log(`Loading ToggleActionButton component`);
import { reactive } from 'vue';

// Define PROPS
const props = defineProps({
  // Get action labels
  labels: Array,
  // Get actions to perform
  actions: Array,
});

// Define emits
const emit = defineEmits(['doAction']);

// Make reactive vars
const reacts = reactive({
  currentLabel: props.labels[0],
  action: props.actions[0],
});

// Set initital action states
let actionState = false;
let action = props.actions[0];

// Change label and action, send action to parent
function toggleActionState() {
  console.log(`Action State is: ${actionState}`);

  // Send action to parent
  emit('doAction', reacts.action);

  // Toggle between action states for next click
  console.log(`Toggle Label: ${reacts.currentLabel} `);
  console.log(`Toggle Action: ${reacts.action} `);

  if (!actionState) {
    reacts.currentLabel = props.labels[1];
    reacts.action = props.actions[1];
  } else {
    reacts.currentLabel = props.labels[0];
    reacts.action = props.actions[0];
  }

  // Change state to opposite of previous
  actionState = !actionState;
}
</script>

<style scoped></style>
