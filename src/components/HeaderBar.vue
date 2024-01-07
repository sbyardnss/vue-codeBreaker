<script lang="ts">
import type { PropType } from 'vue';

export default {
    name: "HeaderBar",
    emits: ["refreshClicked"],
    props: {
        codeSolved: {
            type: Boolean,
            required: true
        },
        correctCodeForDisplay: {
            type: Array as PropType<string[]>,
            required: true
        },
        getClass: {
            type: Function,
            required: true
        }
    },
    methods: {
        handleRefreshClicked() {
            this.$emit("refreshClicked")
        }
    },
    computed: {
        flipCardClass() {
            return !this.codeSolved ? "flipCard" : "flipCardSolved"
        }
    }
}
</script>
<template>
    <section :id="$style.headerContainer">
        <!-- Flip card container -->
        <div :id="$style.flipCardContainer">
            <div :class="$style[flipCardClass]">
                <!-- flip card front -->
                <div :class="$style['flipCardFront']">
                    <h1>Mastermind</h1>
                </div>
                <!-- flip card back -->
                <div :class="$style['flipCardBack']">
                    <ul :class="$style['correctCodeDisplay']" v-if="codeSolved">
                        <li :key="color" v-for="(color) in correctCodeForDisplay" :class="[getClass(color)]"></li>
                    </ul>
                </div>
            </div>
        </div>
        <button :id="$style.refreshButton" @click="handleRefreshClicked()">Restart</button>
    </section>
</template>
<style module>
#headerContainer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    /* height: 5em; */
    height: 10%;
    width: 98%;
    margin: .25em 0;
    /* border: 1px solid orange; */
    font-size: 1.9vh;
}
h1 {
    font-size: 6vh;
}
#flipCardContainer {
    /* width: 98%;
    height: 100%; */
    width: 70%;
    z-index: 10;
}

#refreshButton {
    height: 100%;
    width: 25%;
    text-align: center;
    font-size: 2vh;
    background-color: white;
    border: .1em solid gray;
    border-radius: 2vh;
}

.correctCodeDisplay {
    background-color: white;
    border-radius: 10px;
    height: 5em;
    display: flex;
    justify-content: center;
    align-items: center;
    list-style: none;
    padding: 0;
    margin: 0;
    width: 18em;
}

.flipCard {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform .75s;
    transform-style: preserve-3d;
}

.flipCardSolved {
    position: relative;
    width: 100%;
    height: 100%;
    transform: rotateX(180deg);
    transition: transform .75s;
    transform-style: preserve-3d;
}

/* Position the front and back side */
.flipCardFront,
.flipCardBack {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    /* Safari */
    backface-visibility: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

.flipCardFront {
    background-color: white;
    color: black;
}

.flipCardBack {
    background-color: #517fa4;
    color: black;
    transform: rotateX(180deg);

}

.flipCardFront img {
    width: 100%;
    height: 100%;
}

.flipCardBack p {
    text-align: center;
    margin: 1rem;
    font-size: 1.4rem;
    line-height: 1.5rem;
}

.flipCardBack p span {
    display: block;
    font-size: 1rem;
    font-style: italic;
    font-weight: bold;
    margin-top: 1.25rem;
}
</style>