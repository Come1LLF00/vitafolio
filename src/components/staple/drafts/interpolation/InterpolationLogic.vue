<template>
  <div class='interpolation-logic'>
    L_n = {{ Lagrange }}
  </div>
</template>

<script>
  export default {
    name: 'InterpolationLogic',

    data: function() {
      return {
        Lagrange: '',
      };
    }, 

    props: {
      'X': Array,
      'Y': Array,
      'x0': Number,
    },

    methods: {
      c_i: function( i, X, Y ) {
        let denominator = 1;
        for ( let j = 0; j < X.length; ++j )
          if ( i != j )
            denominator *= ( X[ i ] - X[ j ] );

        return Y[ i ] / denominator;
      },

      c_n: function( X, Y ) {
        let C_n = [];
        for ( let i = 0; i < X.length; ++i )
          C_n.push( this.c_i( i, X, Y ) );
        return C_n;
      },

      l_i: function( X, Y, i, c_i, x0 ) {
        let product = c_i;
        for ( let j = 0; j < X.length; ++j )
          if ( i != j )
            product *= ( x0 - X[ j ] );
        return product;
      },

      l_n: function( X, Y, x0 ) {
        let C_n = this.c_n( X, Y );
        let L_n = [];
        for ( let i = 0; i < X.length; ++i )
          L_n.push( this.l_i( X, Y, i, C_n[ i ], x0 ) );
        return L_n;
      },

      L_n: function( X, Y, x0 ) {
        return ( this.l_n( X, Y, x0 ) ).reduce( ( accumulator, curr ) => accumulator + curr );
      },

      calculate: function( X, Y, x0 ) {
        console.log( 'recalculations initiated' );
        this.Lagrange = this.L_n( X, Y, x0 );
      },
    },

    watch: {
      X: {
        handler: function() {
          this.calculate( this.X, this.Y, this.x0 );
        },

        deep: true,
      },

      Y: {
        handler: function() {
          this.calculate( this.X, this.Y, this.x0 );
        },

        deep: true,
      },

      x0: function() {
        this.calculate( this.X, this.Y, this.x0 );
      },
    },
  }
</script>

<style scoped>
</style>