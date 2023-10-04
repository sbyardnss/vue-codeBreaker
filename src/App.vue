<script setup lang="ts">
import Attempts from './components/Attempts.vue'
import CodeInput from './components/CodeInput.vue';
import CurrentAttempt from './components/CurrentAttempt.vue';
import HeaderBar from './components/HeaderBar.vue';
import { reactive, ref, onMounted } from 'vue';
import type { Ref } from 'vue';
let attemptsForListComponent: Ref<string[][]> = ref([])
let currentAttempt: Ref<string[]> = ref([])
const appColorChoices = ['red', 'orange', 'yellow', 'green', 'blue', 'violet']
let availableColorChoices: Ref<string[]> = ref([])
let correctCode: Ref<string[]> = ref([])
let solved: Ref<boolean> = ref(false)
function createNewCode() {
  const newCode: string[] = []
  // newCode.push('bill')
  const copyColorChoices = [...appColorChoices]
  for (let i = 0; i < 4; i++) {
    const randomIndex = Math.floor(Math.random() * copyColorChoices.length)
    const selectedColor = copyColorChoices.splice(randomIndex, 1)[0]
    newCode.push(selectedColor)
  }
  correctCode.value = newCode
}
onMounted(() => {
  createNewCode()
  availableColorChoices.value = [...appColorChoices]
  console.log(correctCode.value)

})
function refreshCode() {
  createNewCode()
  availableColorChoices.value = [...appColorChoices]
  attemptsForListComponent.value = []
  currentAttempt.value = []
  solved.value = false
  console.log(correctCode.value)
}
function getClass(color: string): string {
  return `${color}Circle`
}
function checkIfNewCodeIsCorrect(code: string[]) {
  const codeString = code.toString()
  const correctCodeString = correctCode.value.toString()
  if (codeString === correctCodeString) {
    solved.value = true
    console.log('solved')
  }

}

//add colors to current attempt
function handleCurrentCodeUpdated(addedColor: string) {
  if (currentAttempt.value.indexOf("blank") !== -1) {
    const blankIndex = currentAttempt.value.indexOf("blank")
    currentAttempt.value.splice(blankIndex, 1, addedColor)
  }
  else {
    currentAttempt.value.push(addedColor)
  }
  const indexOfAddedColor = availableColorChoices.value.indexOf(addedColor)
  availableColorChoices.value.splice(indexOfAddedColor, 1, "blank")

  if (currentAttempt.value.filter(a => a !== "blank").length === 4) {
    checkIfNewCodeIsCorrect(currentAttempt.value)
    attemptsForListComponent.value.push([...currentAttempt.value]);
    currentAttempt.value.splice(0, currentAttempt.value.length)
    availableColorChoices.value = [...appColorChoices]

  }

}

//remove colors from current attempt
function handleColorRemoved(removedColor: string) {
  const colorIndex = currentAttempt.value.indexOf(removedColor)
  if (currentAttempt.value.length > 1) {
    currentAttempt.value.splice(colorIndex, 1, "blank")
  }
  else {
    currentAttempt.value.splice(colorIndex, 1)
  }
  const indexOfColorInAppChoices = appColorChoices.indexOf(removedColor)
  availableColorChoices.value.splice(indexOfColorInAppChoices, 1, removedColor)
}

</script>
<template>
  <!-- <h1 :class="[$style.header]">Hello World</h1> -->
  <main :id="$style.appContainer">
    <HeaderBar :codeSolved="solved" :correctCodeForDisplay="correctCode" :getClass="getClass" @refreshClicked="refreshCode"/>
    <Attempts :attemptedCodes="attemptsForListComponent" :getClass="getClass" :correctCodeForReference="correctCode"/>
    <CurrentAttempt :currentCodeAttempt="currentAttempt" :getClass="getClass" @colorRemoved="handleColorRemoved" />
    <CodeInput :getClass="getClass" :colorChoices="availableColorChoices" @colorAdded="handleCurrentCodeUpdated" />
  </main>
</template>
<style module>
.header {
  color: blue;
}

#appContainer {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* border: 1px solid black; */
  border: 2px solid gray;

  border-radius: 12px;
  width: fit-content;
  margin: 0;
}

</style>
