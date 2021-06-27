<template>
  <div class="brief">
    <div class='brief__info'>
      <img class='brief__image--round' alt='Brief logo' src='../../assets/staple/guest.png'/>
      <div class='brief__text'>
        <h4 class='brief__fullname brief__text--biased'>Lenar Khannanov</h4>
        <h5 class='brief__nickname brief__text--biased'>@comeillfoo</h5>
      </div>
    </div>
    <div class='brief-switcher'>
      <a class='plain-btn' @click='$emit( "update:is_about", !is_about )' >Go to {{ goto }}</a>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Brief',

    props: {
      'is_about': Boolean
    },

    computed: {
      goto: function() {
        return this.is_about? 'storage' : 'about';
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .brief {
    text-align: left;
    border-bottom: 1px solid;
    padding-bottom: 0.8rem;
  }

  .brief__image--round {
    border-radius: 5em;
    border: 1px solid rgba( 0, 0, 0, 0.3 );
    width: 4rem;
  }

  .brief__info {
    display: inline-block;
    margin-left: 1.33rem;
    width: 70rem;
  }

  .brief__text {
    margin-left: 1rem;
    text-align: left;
    display: inline-block;
    vertical-align: top;
    padding-top: 0.66rem;
  }

  .brief__text--biased {
    margin: 0.2rem;
  }

  .brief-switcher {
    margin-right: 0.5rem;
    display: inline-block;
    vertical-align: top;
    padding-top: 0.66rem;
  }
</style>
