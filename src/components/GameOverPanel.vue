<template>
    <div id="game-over-panel">
        <div id="game-over-title"></div>
    </div>
</template>

<script>
export default {
    name: "GameOverPanel",
    props: {
        score: {
            type: Number,
            required: true,
        },
    },
};
</script>

<style></style>
