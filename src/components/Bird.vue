<template>
    <div
        :style="{ bottom: birdStyle.bottom + 'px', left: birdStyle.left + 'px' }"
        class="bird"
    ></div>
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
