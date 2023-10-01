<script lang="ts">
import type { PropType } from 'vue';

export default {
    name: "Attempts",
    props: {
        attemptedCodes: {
            type: Array as PropType<string[][]>,
            required: true
        }
    },
    methods: {
        getClass(color: string): string {
            return `${color}Circle`
        }
    }

}
interface AttemptedCodes {
    attemptedCodes: string[][];
} 
</script>
<template>
    <h2>here are your attempts</h2>
    <div :id=$style.attemptListContainer>
        <ul :id=$style.attemptList v-for="list in attemptedCodes">
            <li v-for="color in list" :class="$style[getClass(color)]"></li>
        </ul>
    </div>
</template>
<style module>
#attemptListContainer {
    background-color: gray;
    height: 80vh;
}

#attemptList {
    list-style: none;
    display: flex;
    width: 100%;
}

.redCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: red;
}

.blackCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: black;
}

.blueCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: blue;
}

.purpleCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: purple;
}

.orangeCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: orange;
}

.greenCircle {
    height: 2em;
    width: 2em;
    border-radius: 50%;
    background-color: green;
}
</style>