<template>
    <h3>{{title}}</h3>
    <h4>Reaction Time: {{ score }} ms</h4>
    <h1 class="done">{{rank}}</h1>
</template>

<script>


export default {
    props: ['score'],
    data() {
        return {
            title: 'Your Results',
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = 'Ninja Fingers'
        } else if (this.score < 400) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Too Slow'
        }
    }
}
</script>

<style>
    .done {
        border-radius: 7px;
        border: 2px solid #b6b6b6;
        padding: 8px 20px;
        background: #fbffc7; 
    }

</style>