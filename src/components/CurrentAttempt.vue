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
    <div :id="$style.currentAttemptContainer">
        <h3 :class="[$style.header]">current attempt</h3>
        <ul :id=$style.currentAttemptDisplay>
            <li v-for="(color, index) in currentCodeAttempt" :class="$style[getClass(color)]" @click="emitRemoveColor(index)"></li>
        </ul>
    </div>
</template>
<style module>
.header {
    margin: .5em 0 0 0;
}
#currentAttemptContainer {
    margin-top: 1em;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
}
#currentAttemptDisplay {
    background-color: gray;
    border-radius: 10px;
    height: 5em;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    list-style: none;
    padding: 0;
    margin-top: 0;
    width: 18em;
}

.redCircle {
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
    border: 2px solid lightgray;
    border-radius: 50%;
    background-color: lightgray;
    margin: 0 .5em;
    box-shadow: rgba(255, 255, 255 ) 0 1px 10px inset;

}
</style>