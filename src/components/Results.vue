<template>
  <p>Reaction time: {{ score }} ms</p>
</template>

<script>
export default {
    // Accept a score prop from App.vue
props: ['score']
}
</script>

<style>

</style>