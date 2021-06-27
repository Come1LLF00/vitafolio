<template>
  <div id="app">
    <Welcome v-if="is_not_started" :is_not_started.sync='is_not_started' />
    <Staple v-else />
  </div>
</template>

<script>
  import Welcome from './components/Welcome.vue'
  import Staple from './components/Staple.vue'
  import Anychart from 'anychart'

  export default {
    name: 'App',
    components: {
      Welcome,
      Staple,
    },
    data: function() {
      return {
        is_not_started: true,
        Anychart: Anychart,
      }
    },
  }
</script>

<style>
  /* the most convenient measurements way */
  *, *:before, *:after {
    box-sizing: border-box;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .plain-btn {
    text-transform: uppercase;
    border: 1px solid;
    border-radius: 2rem;
    padding: 0.75rem 1.3rem;
    font-weight: 600;
    text-align: center;
    display: inline-block;
  }
</style>
