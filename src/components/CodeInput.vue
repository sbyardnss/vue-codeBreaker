<script lang="ts">
import type { PropType } from 'vue';
export default {
    name: "CodeInput",
    emits: ["colorAdded"],
    props: {
        getClass: {
            type: Function,
            required: true
        },
        colorChoices: {
            type: Array as PropType<string[]>,
            required: true
        },
    },
    methods: {
        handleColorClicked(color: string) {
            this.$emit("colorAdded", color)
        }
    }
}
</script>
<template>
    <div :id="$style.inputContainer">
        <h3 :class="$style.header">select colors</h3>
        <ul :id="$style.choicesContainer">
            <li v-for="color of colorChoices" :class="$style[getClass(color)]" @click="handleColorClicked(color)"></li>
        </ul>
    </div>
</template>
<style module>
#inputContainer {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    width: 100%;

}

.header {
    margin: .5em 0 0 0;
}

#choicesContainer {
    background-color: lightgray;
    border-radius: 10px;
    height: 5em;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    list-style: none;
    padding: 0;
    margin: 0;
    width: 100%;
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
    border: 2px solid rgb(196, 196, 196);
    border-radius: 50%;
    background-color: rgb(138, 138, 138);
    margin: 0 .5em;
    box-shadow: rgb(196, 196, 196) 0 1px 10px inset;

}</style>