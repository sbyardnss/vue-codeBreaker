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
            <!-- flip card front -->
            <div :class="$style[flipCardClass]">
                <div :class="$style['flipCardFront']">
                    <h1>Mastermind</h1>
                </div>
                <!-- flip card back -->
                <div :class="$style['flipCardBack']">
                    <ul :class="$style['correctCodeDisplay']" v-if="codeSolved">
                        <li v-for="(color) in correctCodeForDisplay" :class="$style[getClass(color)]"></li>
                    </ul>
                </div>
            </div>
        </div>
        <div :id="$style.refreshButtonContainer">
            <button :id="$style.refreshButton" @click="handleRefreshClicked()">Refresh</button>
        </div>
    </section>
</template>
<style module>
#headerContainer {
    display: flex;
    align-items: center;
    height: 5em;
}

#flipCardContainer {
    width: 20em;
    /* height: 400px; */
    /* perspective: 1000px; */
    z-index: 10;
}

#refreshButton {
    height: 5em;
    width: 6.6em;
    background-color: white;
    border: 2px solid gray;
    border-radius: 10px;
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
    /* margin-top: 0; */
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
    /* border-radius: 0.5rem; */
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
    /* border-radius: 0.5rem; */
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