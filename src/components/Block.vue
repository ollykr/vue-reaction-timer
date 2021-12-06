<template>
<!-- Show a green block only if "showBlock" is true -->
  <div class="block" v-if="showBlock">Click Me</div>
</template>

<script>
export default {
// Take in a prop "delay" that I want to receive from App.vue
props: ['delay'],
data() {
  return {
    // By default showBlock is false, so after clicking "play", 'mounted' hook fires up showing "component mounted", timer (timeout) inside 'mounted" hook starts, "block" div will be shown after a certain "delay" we set in timer inside 'mounted' hook, the div is shown after 'shoBlock' boolean set to 'true'
showBlock : false
  }
},
// Place lifecycle hooks/methods directly in the component object
// Hook mounted to DOM
// It will be fired on clicking "Play"
mounted() {
// the code will fire only when the hook mounted to the DOM
console.log('component mounted')
setTimeout(() => {
  this.showBlock = true
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
// }
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