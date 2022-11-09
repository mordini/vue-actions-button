<!-- "I can do all things through him who strengthens me." -Philippians 4:13 -->
<template>
  <div class="">
    <button
      style="outline: none"
      @click="runActionByType()"
      class="button"
      :class="[props.styles, reacts.colour]"
    >
      {{ reacts.currentLabel }}
    </button>
    <!-- <p>{{ reacts.action }}</p> -->
  </div>
</template>
<script setup>
console.log(`Loading ActionsButton component`);
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

// Set initital action states
let actionState = false;

// Define emits
const emit = defineEmits(['doAction']);

// Make reactive vars
const reacts = reactive({
  currentLabel: props.labels[0],
  action: props.actions[0],
  colour: props.colour[0],
});

// Run one action, or toggle between two
function runActionByType() {
  // Bool for multiple actions
  console.log(props.actions);
  let toggleActions = props.actions.length > 1;

  console.log(`toggle actions is: ${toggleActions}`);

  toggleActions ? runToggleAction() : runSingleAction();
  console.log(`toggle actions is: ${toggleActions}`);
}

// Run the single action, send to parent
function runSingleAction() {
  console.log(`running single action: ${props.actions[0]}`);
  reacts.action = props.actions[0];
  emit('doAction', reacts.action);
}

// Run the toggle actions

// Change label and action, send action to parent
function runToggleAction() {
  console.log(`running toggle action: ${reacts.action}`);

  // Send action to parent
  emit('doAction', reacts.action);

  // Actions between action states for next click
  if (actionState) {
    reacts.currentLabel = props.labels[0];
    reacts.action = props.actions[0];
    reacts.colour = props.colour[0];
  } else {
    reacts.currentLabel = props.labels[1];
    reacts.action = props.actions[1];
    reacts.colour = props.colour[1];
  }

  // Change state to opposite of previous
  actionState = !actionState;
}
</script>

<style scoped></style>
