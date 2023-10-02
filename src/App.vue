<script setup lang="ts">
import Attempts from './components/Attempts.vue'
import CodeInput from './components/CodeInput.vue';
import CurrentAttempt from './components/CurrentAttempt.vue';
import HeaderBar from './components/HeaderBar.vue';
import { reactive, ref, onMounted } from 'vue';
import type { Ref } from 'vue';
const attemptsForListComponent: Ref<string[][]> = ref([])
let currentAttempt: Ref<string[]> = ref([])
const appColorChoices = ['red', 'orange', 'yellow', 'green', 'blue', 'violet']
let correctCode: Ref<string[]> = ref([])
let solved: Ref<boolean> = ref(false)
function createNewCode() {
  const newCode: string[] = []
  // newCode.push('bill')
  for (let i = 0; i < 4; i++) {
    const randomIndex = Math.floor(Math.random()*6)
    const selectedColor = appColorChoices[randomIndex]
    newCode.push(selectedColor)
  }
  correctCode.value = newCode
}
onMounted(() => {
  createNewCode()
  console.log(correctCode.value)
})
function getClass(color: string): string {
  return `${color}Circle`
}
function checkIfNewCodeIsCorrect(code: string[]) {
  const codeString = code.toString()
  const correctCodeString = correctCode.value.toString()
  if (codeString === correctCodeString) {
    solved.value = true
  }

}
function handleCurrentCodeUpdated(color: string) {
  if (currentAttempt.value.indexOf("blank") !== -1) {
    const blankIndex = currentAttempt.value.indexOf("blank")
    currentAttempt.value.splice(blankIndex, 1, color)
  }
  else {
    currentAttempt.value.push(color)
  }
  if (currentAttempt.value.filter(a => a !== "blank").length === 4) {
    checkIfNewCodeIsCorrect(currentAttempt.value)
    attemptsForListComponent.value.push([...currentAttempt.value]);
    currentAttempt.value.splice(0, currentAttempt.value.length)
  }
}
function handleColorRemoved(index: number) {
  currentAttempt.value.splice(index, 1, "blank")
}

</script>
<template>
  <!-- <h1 :class="[$style.header]">Hello World</h1> -->
  <main :id="$style.appContainer">
    <HeaderBar />
    <Attempts :attemptedCodes="attemptsForListComponent" :getClass="getClass" />
    <CurrentAttempt :currentCodeAttempt="currentAttempt" :getClass="getClass" @colorRemoved="handleColorRemoved" />
    <CodeInput :getClass="getClass" :colorChoices="appColorChoices" @colorAdded="handleCurrentCodeUpdated" />
  </main>
</template>
<style module>
.header {
  color: blue;
}

#appContainer {
  display: flex;
  flex-direction: column;
}
</style>
