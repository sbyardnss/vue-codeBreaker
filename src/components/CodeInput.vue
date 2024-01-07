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
            console.log(color);
            this.$emit("colorAdded", color)
        }
    }
}
</script>
<template>
    <div :id="$style.inputContainer">
        <h3 :class="$style.header">select colors</h3>
        <ul :id="$style.choicesContainer">
            <li :key="color" v-for="color of colorChoices" :class="[getClass(color)]" @click="handleColorClicked(color)"></li>
        </ul>
    </div>
</template>
<style module>
#inputContainer {
    display: flex;
    flex-direction: column;
    /* justify-content: space-evenly; */
    width: 98%;
    height: 15%;
    margin-bottom: 2%;
    /* font-size: 1.9vh; */
}

.header {
    /* height: 20%; */
    margin: 0;
}

#choicesContainer {
    background-color: lightgray;
    border-radius: 1.2vh;
    height: 70%;
    /* height: 6em; */
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    list-style: none;
    padding: 0;
    margin: 0;
    width: 100%;
    font-size: 2vh;
    /* height: 3em; */
    /* height: 100%; */
    /* max-height: 80px; */
}

</style>