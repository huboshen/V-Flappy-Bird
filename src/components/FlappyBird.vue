<template>
    <div id="flappy-bird-wrapper" class="">
        <div id="background" class="night">
            <bird></bird>
            <pipe></pipe>
        </div>
        <div id="ground"></div>
    </div>
</template>

<script>
import Pipe from "@/components/Pipe";
import Bird from "@/components/Bird";
export default {
    name: "FlappyBird",
    components: {
        Pipe,
        Bird,
    },
    props: {},
};
</script>

<style lang="scss" scoped>
@import "~@/assets/images/flappy-bird/scss/flappy-bird.scss";
</style>
