<template>
    <div id="game-over-panel">
        <div id="current-score-box">
            <div
                v-for="(d, i) in scoreDigits"
                :key="i"
                :class="`digit-${d}`"
            ></div>
            <div class="label-new" v-if="hasBreakRecord"></div>
        </div>
        <transition name="fade">
            <div id="game-over-title" v-show="showGameOverTitle"></div>
        </transition>
    </div>
</template>

<script>
export default {
    name: "GamePanel",
    props: {
        showGameOverTitle: {
            type: Boolean,
            required: true,
        },
        score: {
            type: Number,
            required: true,
        },
        hasBreakRecord: {
            type: Boolean,
            default: false,
        },
    },
    computed: {
        scoreDigits() {
            return Array.from(String(this.score), Number);
        },
    },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
}
</style>
