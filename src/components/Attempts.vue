<script lang="ts">
import type { PropType } from 'vue';

export default {
    name: "Attempts",
    props: {
        attemptedCodes: {
            type: Array as PropType<string[][]>,
            required: true
        },
        getClass: {
            type: Function,
            required: true
        }
        
    }
}
interface AttemptedCodes {
    attemptedCodes: string[][];
} 
</script>
<template>
    <!-- <h2>here are your attempts</h2> -->
    <div :id=$style.attemptListContainer>
        <ul :id=$style.attemptList v-for="list in attemptedCodes">
            <li v-for="color in list" :class="$style[getClass(color)]"></li>
        </ul>
    </div>
</template>
<style module>
#attemptListContainer {
    background-color: gray;
    height: 60vh;
    width: 20em;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#attemptList {
    list-style: none;
    display: flex;
    padding: 0;
    /* width: 100%; */
    margin: .5em 0 0 0;
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
</style>