<script lang="ts">
import type { PropType } from 'vue';

export default {
    name: "AccuracyCount",
    props: {
        attempt: {
            type: Array as PropType<string[]>,
            required: true
        },
        correctCode: {
            type: Array as PropType<string[]>,
            required: true
        }
    },
    methods: {
        displayAccuracy(attempt: string[], correct: string[]) {
            let correctPlaceAndColorCount = 0
            let correctColorOnlyCount = 0
            let entirelyIncorrect = 0
            for (const selectedColor of attempt) {
                let bothCorrect = false
                let oneCorrect = false
                if (correct.find((color: string) => color === selectedColor)) {
                    let colorIndex = attempt.indexOf(selectedColor)
                    if (colorIndex === correct.indexOf(selectedColor)) {
                        bothCorrect = true
                    }
                    else {
                        oneCorrect = true
                    }
                }
                if (bothCorrect) {
                    correctPlaceAndColorCount++
                }
                if (oneCorrect) {
                    correctColorOnlyCount++
                }
            }
            entirelyIncorrect = 4 - (correctColorOnlyCount + correctPlaceAndColorCount)
            return { entirelyIncorrect, correctPlaceAndColorCount, correctColorOnlyCount }
        }
    },
    computed: {
        accuracyCounts() {
            return this.displayAccuracy(this.attempt, this.correctCode)
        }
    }
}
</script>
<template>
    <div :id="$style.accuracyFlex">
        <span v-for="n in accuracyCounts.correctPlaceAndColorCount" :class="$style.correctPlaceAndColor"></span>
        <span v-for="n in accuracyCounts.correctColorOnlyCount" :class="$style.correctColorOnly"></span>
        <span v-for="n in accuracyCounts.entirelyIncorrect" :class="$style.incorrect"></span>
    </div>
</template>
<style module>
#accuracyFlex {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    width: 100%;
    height: 100%;
    padding-top: .25em;
}
.correctPlaceAndColor {
    background-color: black;
    height: 1em;
    width: 1em;
    border-radius: 50%;
    margin: .25em .5em;
    
}
.correctColorOnly {
    background-color: gray;
    height: 1em;
    width: 1em;
    border-radius: 50%;
    margin: .25em .5em;
}
.incorrect {
    background-color: white;
    height: 1em;
    width: 1em;
    border-radius: 50%;
    margin: .25em .5em;
    box-shadow: rgb(155, 155, 155) 0 1px 10px inset;

}

</style>