<template>
    <div id="ground">
        <div id="best-score-box">
            <div
                v-for="(d, i) in bestScoreDigits"
                :key="i"
                :class="`digit-sm-${d}`"
            ></div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Ground",
    props: {
        bestScoreDigits: {
            type: Array,
            required: true,
        },
    },
};
</script>

<style></style>
