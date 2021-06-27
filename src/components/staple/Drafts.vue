<template>
  <div class='drafts'>
    <div class='drafts__sidebar'>
      <ul class='drafts__list'>
        <li v-for='( item, index ) in items' :key='index' v-bind:class='{ "drafts__sidebar--selected-item": item.is_active }' @click='select( index )'><a>{{ item.title }}</a></li>
      </ul>
    </div>
    <div class='drafts__app'>
      <SystemsOfLinearEquations v-show='items[ "SystemsOfLinearEquations" ].is_active' />
      <NonLinearEquations v-show='items[ "NonLinearEquations" ].is_active' />
      <NumericalIntegration v-show='items[ "NumericalIntegration" ].is_active' />
      <Approximation v-show='items[ "Approximation" ].is_active' />
      <Interpolation v-show='items[ "Interpolation" ].is_active' />
      <Derivation v-show='items[ "Derivation" ].is_active' />
    </div>
  </div>
</template>

<script>
  import SystemsOfLinearEquations from './drafts/SystemsOfLinearEquations.vue'
  import NonLinearEquations from './drafts/NonLinearEquations.vue'
  import NumericalIntegration from './drafts/NumericalIntegration.vue'
  import Approximation from './drafts/Approximation.vue'
  import Interpolation from './drafts/Interpolation.vue'
  import Derivation from './drafts/Derivation.vue'

  export default {
    name: 'Drafts',

    components: {
      SystemsOfLinearEquations,
      NonLinearEquations,
      NumericalIntegration,
      Approximation,
      Interpolation,
      Derivation
    },

    data: function() {
      return {
        items: {
          'SystemsOfLinearEquations': { title: 'Решение систем линейных алгебраических уравнений', is_active: false },
          'NonLinearEquations': { title: 'Численное решение нелинейных уравнений',                 is_active: false },
          'NumericalIntegration': { title: 'Численное интегрирование',                             is_active: false },
          'Approximation': { title: 'Аппроксимация функции методом наименьших квадратов',          is_active: false },
          'Interpolation': { title: 'Интерполяция функции',                                        is_active: false },
          'Derivation': { title: 'Численное дифференцирование',                                    is_active: false },
        },
      };
    },

    methods: {
      select: function( selected ) {
        Object.entries( this.items ).forEach( entry => {
          const [ key, value ] = entry;
          if ( key != selected )
            value.is_active = false;
        } );
        this.items[ selected ].is_active = !this.items[ selected ].is_active;
      },
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .drafts {
    text-align: left;
  }

  .drafts__sidebar {
    display: inline-block;
    width: 20rem;
    /* border-right: 1px solid; */
    border-left: 1px solid;
  }

  .drafts__sidebar ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .drafts__sidebar li {
    border-bottom: 1px solid;
    font-size: 0.8rem;
    padding: 1rem 0.75rem;
  }

  .drafts__sidebar li:hover,
  .drafts__sidebar--selected-item {
    background-color: rgba( 0, 0, 0, 0.2 );
    /* sorry, but without important this shit doesn't keep left offset while selecting it */
    padding-left: 1.5rem !important;
  }

  .drafts__app {
    min-height: 318px;
    display: inline-block;
    border-left: 1px solid;
    vertical-align: top;
    padding: 1rem;
  }
</style>
