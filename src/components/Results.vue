<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    // Accept a score prop from App.vue
props: ['score'],
data() {
    return {
        rank: null
    }
},
// When it mounts, we look at the score ('score'), and display data depending on do if else
mounted() {
    // check the score
    if(this.score < 250) {
this.rank = 'Ninja Fingers'
    } else if (this.score < 400) {
        this.rank = 'Rapid Reflexes'
    } else {
        this.rank = 'Snail pace...'
    }
}
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>