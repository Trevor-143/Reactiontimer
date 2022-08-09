<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Fast</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
        // console.log('components mounted')
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        width: 500px;
        padding: 70px;
        background: #8c0000;
        border-radius: 15px;
        margin: 20px;
        text-align: center;
        color: #ffffff;
    }
</style>