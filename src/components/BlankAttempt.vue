<script lang="ts">
export default {
    name: "BlankAttempt"
}
</script>
<template>
        <ul :class="$style['attemptList']">
            <li v-for="n in 4" :class="$style['blankCircle']"></li>
        </ul>
        <div :id="$style.accuracyContainer">
            <!-- <AccuracyCountVue :attempt="list" :correctCode="correctCodeForReference" /> -->
        </div>
</template>
<style module>
#attemptListWithAccuracy {
    display: flex;
    width: 100%;
    height: 4em;
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
    /* margin: .5em 0 0 0; */

}

#accuracyContainer {
    /* display: flex; */
    width: 20%;
    height: 100%;
    /* margin: .5em; */
    border: 1px solid gray;
    background-color: lightgray;
    border-radius: 8px;
    justify-self: flex-end;
}

.blankCircle {
    height: 3em;
    width: 3em;
    border: 2px solid rgb(196, 196, 196);
    border-radius: 50%;
    background-color: rgb(138, 138, 138);
    margin: 0 .5em;
    box-shadow: rgb(196, 196, 196) 0 1px 10px inset;

}
</style>