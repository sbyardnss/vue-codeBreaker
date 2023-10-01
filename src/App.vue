<script setup lang="ts">
import Attempts from './components/Attempts.vue'


const attemptsForListComponent: string[][]= []
</script>
<template>
  <h1 :class="[$style.header]">Hello World</h1>
  <Attempts :attemptedCodes="attemptsForListComponent"/>
</template>
<style module>
.header {
  color: blue;
}
</style>
