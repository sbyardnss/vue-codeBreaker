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
    height: 25%;
    margin-bottom: .25em;

}

.header {
    /* height: 20%; */
    margin: .25em 0 0 0;
}

#choicesContainer {
    background-color: lightgray;
    border-radius: 10px;
    height: 70%;
    /* height: 6em; */
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    list-style: none;
    padding: 0;
    margin: 0;
    width: 100%;
    font-size: 3vw;
    /* height: 3em; */
    /* height: 100%; */
    /* max-height: 80px; */
}

/* .redCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: red;
    margin: 0 .25em;
}

.orangeCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: orange;
    margin: 0 .25em;
}

.yellowCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: yellow;
    margin: 0 .25em;
}

.greenCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: green;
    margin: 0 .25em;
}

.blueCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: blue;
    margin: 0 .25em;
}

.indigoCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: indigo;
    margin: 0 .25em;
}

.violetCircle {
    height: 70%;
    width: 12.5%;
    border: 2px solid black;
    border-radius: 50%;
    background-color: violet;
    margin: 0 .25em;
}

.blankCircle {

    height: 70%;
    width: 12.5%;
    border: 2px solid rgb(196, 196, 196);
    border-radius: 50%;
    background-color: rgb(138, 138, 138);
    margin: 0 .25em;
    box-shadow: rgb(196, 196, 196) 0 1px 10px inset;

} */
</style>