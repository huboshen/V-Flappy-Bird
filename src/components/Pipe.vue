<template>
    <div :style="{ right: pipeStyle.right + 'px' }" class="pipe-wrapper">
        <div
            :style="{ top: pipeStyle.pipeTopTop + 'px' }"
            class="pipe pipe-top"
        ></div>
        <div
            :style="{ top: pipeStyle.pipeBottomTop + 'px' }"
            class="pipe pipe-bottom"
        ></div>
    </div>
</template>

<script>
export default {
    name: "Pipe",
    props: {
        pipeStyle: { type: Object, required: true },
    },
};
</script>

<style lang="scss" scope></style>
