<script lang="ts">
export default {
    name: "BlankAttempt"
}
</script>
<template>
        <ul :class="$style['attemptList']">
            <li :key="'blank' + n" v-for="n in 4" class="blankCircle"></li>
        </ul>
        <div :id="$style.accuracyContainer">
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
    border-radius: 1.2vh;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0;
    width: 75%;
    height: 100%;
    font-size: 1.8vh;

}

#accuracyContainer {
    width: 20%;
    height: 100%;
    border: 1px solid gray;
    background-color: lightgray;
    border-radius: 1.2vh;
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