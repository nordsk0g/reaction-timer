<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" :disabled="isPlaying">Start game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="score" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    }
  },
  components: { Block, Results },
  methods: {
    startGame() {
      this.delay = 1000 + Math.random() * 3000  
      this.isPlaying = !this.isPlaying
      this.score = null;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  padding: 1em 2em;
  border-radius: 0.5em;
  border: none;
  background: #0faf87;
  color: #eee;
  font-family: 'Roboto', sans-serif;
  font-size: 1em;
  letter-spacing: 1px;
  cursor: pointer;
  text-transform: uppercase;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

button:active {
  position: relative;
  top: 2px;
}

</style>
