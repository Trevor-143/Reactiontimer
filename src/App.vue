<template>
  <h1>{{title}}</h1>
  <button @click="go" :disabled="isPlaying">Start</button>
  <Block v-if="isPlaying" :delay="delay" @end="done"></Block>
  <Results  v-if="showResults" :score="score"></Results>
</template>

<script>
import Block from './components/block.vue'
import Results from './components/results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      title: 'Be Quick',
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    go() {
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResults = false
      // console.log(this.delay)
    },
    done(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
  
}
</script>

<style>
body {
  display: flex;
  align-items: center;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #939393;
  margin-top: 60px;
}
button {
  margin: 10px;
  padding: 10px 20px;
  border: none;
  color: #000000;
  background: #f5ffbd;
  border-radius: 5px;
  cursor: pointer;
}
button[disabled] {
  cursor: not-allowed;
}
</style>
