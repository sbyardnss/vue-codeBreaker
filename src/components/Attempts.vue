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
                <li v-if="list.length < 4" v-for="n in 4 - list.length" :key="'blank--' + n" :class="$style.blankCircle"></li> 
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
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#attemptListWithAccuracy {
    display: flex;
    width: 100%;
    height: 10.75%;
    justify-content: space-evenly;
    align-items: center;
    margin-top: .5em;
}

.attemptList {
    list-style: none;
    background-color: gray;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0;
    width: 75%;
    height: 100%;

}

#accuracyContainer {
    width: 20%;
    height: 100%;
    border: 1px solid gray;
    background-color: lightgray;
    border-radius: 8px;
    justify-self: flex-end;
}

/* .redCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: red;
    margin: 0 .5em;
}

.orangeCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: orange;
    margin: 0 .5em;
}

.yellowCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: yellow;
    margin: 0 .5em;
}

.greenCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: green;
    margin: 0 .5em;
}

.blueCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: blue;
    margin: 0 .5em;
}

.indigoCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: indigo;
    margin: 0 .5em;
}

.violetCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: violet;
    margin: 0 .5em;
}

.blankCircle {
    height: 3em;
    width: 3em;
    border: 2px solid rgb(196, 196, 196);
    border-radius: 50%;
    background-color: rgb(138, 138, 138);
    margin: 0 .5em;
    box-shadow: rgb(196, 196, 196) 0 1px 10px inset;
} */
</style>