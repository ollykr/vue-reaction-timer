<template>
<h1>Ninja Reaction Timer</h1>
<!-- "start" is a function name exported below -->
<!-- The button is disabled while we are playing, we can't start a new game while current game is on -->
<button @click="start" :disabled="isPlaying">play</button>
<!-- Add/display Block component -->
<!-- Only display after clicking "Play" -->
<!-- Pass in "delay" property as a prop and bind (v-bind:delay or just :delay) some data (a "delay" property) to it-->
<!-- If we comment the below out after "component mounted" and "component updated" hooks fired up, we will see "unmounted" hook -->
<!-- If we navigate away from a page, "inmounted" hook is also fires up - when we work with Vue router -->
<!-- "end" is a given name for the emit, "endGame" is a function (we created inside methods property) that fires up via the emit -->
<!-- We listen to the event "end" via @end -->
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<!-- Outputting user's score only IF there are results -->
<p v-if="showResults">Reaction time: {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      // Data properties
      isPlaying: false,
      delay: null,
      // Store user reaction time/score in a variable/property "score" and set it to null to begin with
      // "score" gets updated in "endGame" function
      score: null,
      showResults: false
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
      // Hide previous game results when a user clicks "play" 
      this.showResults = false
    },
    // this is the callback functuion fired up when we emit reaction time result from Block.vue
    // Since "reactionTime" is emmited along with "end", we have access to it as the parameter
    endGame(reactionTime) {
      // "score" set to user's reaction time
        this.score = reactionTime,
        // setting to false since user stopped playing
        this.isPlaying = false
        // display results when the game ends
        this.showResults = true
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
