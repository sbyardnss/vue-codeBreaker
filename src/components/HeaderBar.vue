<script lang="ts">
export default {
    name: "HeaderBar"
}
</script>
<template>
    <section :id="$style.headerContainer">
        <div :id="$style.frontHeaderCard">
            <h2>Mastermind</h2>
        </div>
        <div :id="$style.refreshButtonContainer">
            <button :id="$style.refreshButton">Refresh</button>
        </div>
    </section>
</template>
<style module>
#headerContainer {
    /* margin-top: 1em; */
    display: flex;
    align-items: center;
}
#frontHeaderCard {
    text-align: center;
    width: 20em;
}
#refreshButton {
    height: 5em;
    width: 6.6em;
    background-color: white;
    border: 2px solid gray;
    border-radius: 10px;
}
</style>