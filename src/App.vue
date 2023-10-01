<script setup lang="ts">
import Attempts from './components/Attempts.vue'
import CodeInput from './components/CodeInput.vue';
import CurrentAttempt from './components/CurrentAttempt.vue';
import { reactive } from 'vue';
const attemptsForListComponent: string[][] = reactive([])
let currentAttempt: string[] = []
function getClass(color: string): string {
  return `${color}Circle`
}
function handleCurrentCodeUpdated(color: string) {
  currentAttempt.push(color)
  if (currentAttempt.length===5) {
    attemptsForListComponent.push(currentAttempt)
    currentAttempt = []
  }
} 
</script>
<template>
  <h1 :class="[$style.header]">Hello World</h1>
  <Attempts :attemptedCodes="attemptsForListComponent" :getClass="getClass" />
  <CurrentAttempt :currentCodeAttempt="currentAttempt" />
  <CodeInput :getClass="getClass" @colorAdded="handleCurrentCodeUpdated" />
</template>
<style module>
.header {
  color: blue;
}
</style>
