<template>
  <div class='welcome'>
    <img alt='Vitofolio logo' src='../assets/temp-logo.png'>
    <h1>Welcome to Vitafolio</h1>
    <p>your simple storage</p>
    <!-- btn to get to the main component -->
    <a class='plain-btn' @click='$emit( "update:is_not_started", false )'>get started</a>
  </div>
</template>

<script>
  export default {
    name: 'Welcome',
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
