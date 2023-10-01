<script setup lang="ts">
import Attempts from './components/Attempts.vue'
import CodeInput from './components/CodeInput.vue';

const attemptsForListComponent: string[][] = [['red', 'blue']]
function getClass(color: string): string {
  return `${color}Circle`
}
</script>
<template>
  <h1 :class="[$style.header]">Hello World</h1>
  <Attempts :attemptedCodes="attemptsForListComponent" :getClass="getClass"/>
  <CodeInput :getClass="getClass"/>
</template>
<style module>
.header {
  color: blue;
}
</style>
