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
    max-width: 30em;
    border-radius: 10px;
}

#attemptList {
    list-style: none;
    display: flex;
    width: 100%;
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