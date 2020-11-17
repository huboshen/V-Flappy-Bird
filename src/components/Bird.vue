<template>
    <div
        :style="{
            bottom: birdStyle.bottom + 'px',
            left: birdStyle.left + 'px',
            transform: 'rotate(' + birdStyle.rotate + 'deg)',
        }"
        class="bird"
    >
        <div class="bird-flying"></div>
    </div>
</template>

<script>
export default {
    name: "Bird",
    props: {
        birdStyle: { type: Object, required: true },
    },
};
</script>

<style lang="scss" scope></style>
