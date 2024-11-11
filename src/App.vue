<template>
  <h1>vue reaction timer game</h1>
  <button @click="start" :disabled="isPlaying">play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results :score="score" v-if="showResult" />
</template>

<script>
// import components
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  // register components
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true

    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 200px;
}

button {
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: .2;
  cursor: not-allowed !important;
}
</style>
