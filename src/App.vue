<script setup lang="ts">
import Attempts from './components/Attempts.vue'
import CodeInput from './components/CodeInput.vue';
import CurrentAttempt from './components/CurrentAttempt.vue';
import { reactive, ref } from 'vue';
import type { Ref } from 'vue';
const attemptsForListComponent: Ref<string[][]> = ref([])
let currentAttempt: Ref<string[]> = ref([])
function getClass(color: string): string {
  return `${color}Circle`
}
function handleCurrentCodeUpdated(color: string) {
  if (currentAttempt.value.indexOf("blank") !== -1) {
    const blankIndex = currentAttempt.value.indexOf("blank")
    currentAttempt.value.splice(blankIndex, 1, color)
  }
  else {
    currentAttempt.value.push(color)
  }
  if (currentAttempt.value.filter(a => a !== "blank").length === 5) {
    attemptsForListComponent.value.push([...currentAttempt.value]);
    currentAttempt.value.splice(0, currentAttempt.value.length)
  }
}
function handleColorRemoved(index: number) {
  currentAttempt.value.splice(index, 1, "blank")
}
</script>
<template>
  <h1 :class="[$style.header]">Hello World</h1>
  <Attempts :attemptedCodes="attemptsForListComponent" :getClass="getClass" />
  <CurrentAttempt :currentCodeAttempt="currentAttempt" :getClass="getClass" @colorRemoved="handleColorRemoved" />
  <CodeInput :getClass="getClass" @colorAdded="handleCurrentCodeUpdated" />
</template>
<style module>
.header {
  color: blue;
}
</style>
