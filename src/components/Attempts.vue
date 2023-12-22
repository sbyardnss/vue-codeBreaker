<script lang="ts">
import type { PropType } from 'vue';
import AccuracyCountVue from './AccuracyCount.vue';
import BlankAttempt from './BlankAttempt.vue';

export default {
    name: "AttemptList",
    props: {
        attemptedCodes: {
            type: Array as PropType<string[][]>,
            required: true
        },
        getClass: {
            type: Function,
            required: true
        },
        correctCodeForReference: {
            type: Array as PropType<string[]>,
            required: true
        }
    },
    methods: {
        emitRemoveColor(color: string) {
            this.$emit("colorRemoved", color)
        }
    },
    components: { AccuracyCountVue, BlankAttempt }
}
// interface AttemptedCodes {
//     attemptedCodes: string[][];
// } 
</script>
<template>
    <div :id=$style.attemptListContainer>
        <div :key="attemptedCodes.indexOf(list)" :id=$style.attemptListWithAccuracy v-for="list in attemptedCodes">
            <ul :class="$style['attemptList']">
                <li :key="list.indexOf(color)" v-for="color in list" :class="[getClass(color)]" @click="emitRemoveColor(color)"></li>
                <!-- eslint-disable-next-line -->
                <li v-if="list.length < 4" v-for="n in 4 - list.length" :key="'blank--' + n" class="blankCircle"></li> 
            </ul>
            <div :id="$style.accuracyContainer">
                <AccuracyCountVue :attempt="list" :correctCode="correctCodeForReference" />
            </div>
        </div>
        <div :id="$style.attemptListWithAccuracy" v-for="n in 8 - attemptedCodes.length" :key="'attempt--' + n">
            <BlankAttempt />
        </div>
    </div>
</template>
<style module>
#attemptListContainer {
    background-color: lightgray;
    /* height: 36.5em;
    width: 25.5em; */
    height: 75%;
    width: 98%;
    border-radius: 2vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
}

#attemptListWithAccuracy {
    display: flex;
    width: 100%;
    height: 10.5%;
    justify-content: space-evenly;
    align-items: center;
    /* margin-top: 3.25%; */
}

.attemptList {
    list-style: none;
    background-color: gray;
    border-radius: 1.2vh;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0;
    width: 75%;
    height: 100%;
    font-size: 1.8vh;

}

#accuracyContainer {
    width: 20%;
    height: 100%;
    border: 1px solid gray;
    background-color: lightgray;
    border-radius: 1.2vh;
    justify-self: flex-end;
    font-size: 1.8vh;

}

</style>