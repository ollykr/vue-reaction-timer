<template>
  <div class="block">Click Me</div>
</template>

<script>
export default {
// Take in a prop "delay" that I want to receive fro App.vue
props: ['delay'],
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