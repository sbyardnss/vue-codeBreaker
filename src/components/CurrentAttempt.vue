<script lang="ts">
import type { PropType } from 'vue';
export default {
    name: "CurrentAttempt",
    emits: ["colorRemoved"],
    props: {
        currentCodeAttempt: {
            type: Array as PropType<string[]>,
            required: true
        },
        getClass: {
            type: Function,
            required: true
        }
    },
    methods: {
        emitRemoveColor(index: number) {
            this.$emit("colorRemoved", index)
        }
    }
}
</script>
<template>
    <ul :id=$style.currentAttemptContainer>
        <li v-for="(color, index) in currentCodeAttempt" :class="$style[getClass(color)]" @click="emitRemoveColor(index)"></li>
    </ul>
</template>
<style module>
#currentAttemptContainer {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
    max-width: 30em;
    list-style: none;
    padding: 0;
}

.redCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: red;
}

.orangeCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: orange;
}

.yellowCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: yellow;
}

.greenCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: green;
}

.blueCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: blue;
}

.indigoCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: indigo;
}

.violetCircle {
    height: 3em;
    width: 3em;
    border: 2px solid black;
    border-radius: 50%;
    background-color: violet;
}
</style>