<template>
  <div class='staple'>
    <Brief :is_about.sync='is_about' />
    <About v-if='is_about' />
    <Drafts v-else />
  </div>
</template>

<script>
  import Brief from './staple/Brief.vue'
  import About from './staple/About.vue'
  import Drafts from './staple/Drafts.vue'

  export default {
    name: 'Staple',
    components: {
      Brief,
      About,
      Drafts
    },

    data: function() {
      return {
        is_about: true,
      };
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
