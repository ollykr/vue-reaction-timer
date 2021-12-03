<template>
<h1>Ninja Reaction Timer</h1>
<!-- "start" is a function name exported below -->
<!-- The button is disabled while we are playing, we can't start a new game while current game is on -->
<button @click="start" :disabled="isPlaying">play</button>
<!-- Add/display Block component -->
<!-- Only display after clicking "Play" -->
<!-- Pass in "delay" property as a prop and bind (v-bind:delaay or just :delay) some data (a "delay" property) to it-->
<Block v-if="isPlaying" :delay="delay"/>
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start() {
      // 2000ms === 2sec <-- random amount
      // Gives us a random amount of milliseconds between 0 and 5000
      // lest - 2000ms and most - 7000 (2000 + 5000)
      // each time we start a game, it is going to be different amont between 2sec and 7sec 
      this.delay = 2000 + Math.random() * 5000,
      // when we click a play button, the game starts playing
      this.isPlaying = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
