<script lang="ts">
export default {
    name: "HeaderBar",
    emits: ["refreshClicked"],
    props: {
        codeSolved: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        handleRefreshClicked() {
            this.$emit("refreshClicked")
        }
    }
}
</script>
<template>
    <section :id="$style.headerContainer">
        <div :id="$style.frontHeaderCard">
            <h2 v-if="!codeSolved">Mastermind</h2>
            <div v-else>solved</div>
        </div>
        <div :id="$style.refreshButtonContainer">
            <button :id="$style.refreshButton" @click="handleRefreshClicked()">Refresh</button>
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