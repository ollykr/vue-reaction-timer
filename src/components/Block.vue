<template>
<!-- The goal : 
we need to pass a user's time reaction result to App.vue and from App.vue to Results.vue
How? We emit (send) custom event  . When we emit it, we send an extra data along with it, in this case, it is "reactionTime" (so we can access it from App.vue)
 -->
<!-- Show a green block only if "showBlock" is true -->
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
// Take in a prop "delay" that I want to receive from App.vue
props: ['delay'],
data() {
  return {
    // By default showBlock is false, so after clicking "play", 'mounted' hook fires up showing "component mounted", timer (timeout) inside 'mounted" hook starts, "block" div will be shown after a certain "delay" we set in timer inside 'mounted' hook, the div is shown after 'shoBlock' boolean set to 'true'
showBlock : false,
// timer property
// stores exact intervals
// runs every 10ms
timer: null,
// tracking the time it takes user to click on a square
// it increases every 10ms by...10ms so the timer runs in 10ms steps
reactionTime: 0
  }
},
// Place lifecycle hooks/methods directly in the component object
// Hook mounted to DOM
// It will be fired on clicking "Play"
mounted() {
// the code will fire only when the hook mounted to the DOM
setTimeout(() => {
  this.showBlock = true
  this.startTimer()
  // To check how long we were waiting
  // console.log(this.delay)
}, this.delay);
},
// Updated hook
// It fires whenever any data (data() {...}) inside our component is updated
// updated() {
//   console.log('component updated')
// },
// unmounted hook
// it fires up when the whole component was unmpunted from the DOM, not only when the green "block" doesn't show
// unmounted() {
//   console.log('unmounted')
// },
methods: {
  startTimer() {
this.timer = setInterval(() => {
  this.reactionTime += 10
}, 10)
  },
  // When user clicks on a green block, stops the timer
  stopTimer() {
clearInterval(this.timer)
// emit to App.vue, we give it a name 'end' (or whatever) since it is an end of our game, we also send a "reactionTime" data along with it - aka a user's score
this.$emit('end', this.reactionTime)
  }
}

}
</script>

<style>
 .block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>