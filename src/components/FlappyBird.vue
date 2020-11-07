<template>
    <div id="flappy-bird-wrapper" class="">
        <div id="background" ref="background" class="night">
            <bird ref="bird"></bird>
            <pipe v-for="(pipe, i) in pipes" :key="i" :pipe-style="pipe"></pipe>
        </div>
        <div id="ground"></div>
    </div>
</template>

<script>
const PLAYGROUND_DIMENTIONS = {
    width: 288,
    height: 400,
};
const PIPE_DIMENTIONS = {
    width: 52,
    height: 320,
};
const BIRD_DIMENTIONS = {
    width: 34,
    height: 24,
};

// Settings Related to the game difficulty
const SETTINGS = {
    pipeInterval: 120,
    pipeGapMin: 4 * BIRD_DIMENTIONS.height,
    pipeGapMax: 7 * BIRD_DIMENTIONS.height,
};
import Pipe from "@/components/Pipe";
import Bird from "@/components/Bird";
export default {
    name: "FlappyBird",
    components: {
        Pipe,
        Bird,
    },
    data() {
        return {
            pipes: [],
            pipeMover: null,
        };
    },
    props: {},
    methods: {
        // ref: https://stackoverflow.com/questions/4959975/generate-random-number-between-two-numbers-in-javascript
        randomIntFromInterval(min, max) {
            // min and max included
            return Math.floor(Math.random() * (max - min + 1) + min);
        },
        generatePipe() {
            const fixEdge = 30;
            const currentGap = this.randomIntFromInterval(
                SETTINGS.pipeGapMin,
                SETTINGS.pipeGapMax
            );
            const currentExtendOffset = this.randomIntFromInterval(
                0,
                -(-PIPE_DIMENTIONS.height + fixEdge)
            );
            this.pipes.push({
                right: -PIPE_DIMENTIONS.width,
                pipeTopTop:
                    -PIPE_DIMENTIONS.height + fixEdge + currentExtendOffset,
                pipeBottomTop: currentExtendOffset + currentGap,
            });
        },
        movePipe() {
            const backgroundWidth = this.$refs.background.offsetWidth;
            this.pipeMover = setInterval(() => {
                this.pipes.forEach((pipe) => {
                    // remove pipe if is outside of the game left border
                    if (pipe.right >= backgroundWidth) {
                        this.pipes.shift();
                    }

                    if (this.pipes[this.pipes.length - 1].right > SETTINGS.pipeInterval) {
                        this.generatePipe();
                    }
                    pipe.right += 2;
                    console.log(".offsetWidth", backgroundWidth);
                });
            }, 20);
        },
    },
    mounted() {
        this.generatePipe();
        // this.movePipe();
    },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/images/flappy-bird/scss/flappy-bird.scss";
</style>
