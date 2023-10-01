<script lang="ts">
import type { PropType } from 'vue';
export default {
    name: "CodeInput",
    emits: ["colorAdded"],
    props: {
        getClass: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            colorChoices: ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']
        }
    },
    methods: {
        handleColorClicked(color: string) {
            this.$emit("colorAdded", color)
        } 
    }
}
</script>
<template>
    <h2>here is where the user input will go</h2>
    <ul :id="$style.choicesContainer">
        <li v-for="color of colorChoices" :class="$style[getClass(color)]" @click="handleColorClicked(color)"></li>
    </ul>
</template>
<style module>
#choicesContainer {
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