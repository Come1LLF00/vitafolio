<template>
  <div class='interpolation'>
    <h2>Интерполяция функции</h2>
    <InterpolationInput />
  </div>
</template>

<script>
  import InterpolationInput from './interpolation/InterpolationInput.vue'

  export default {
    name: 'Interpolation',
    components: {
      InterpolationInput
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
