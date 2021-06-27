<template>
  <div class='interpolation-input'>
    <form>
      <fieldset>
        <label>Способ задания функции</label>
        <select v-model.number='selected'>
          <option value='0' >Наборы значений ( x, y )</option>
          <option value='1' >Заготовленная функция</option>
        </select>
      </fieldset>
      <fieldset v-if='selected == 1' >
        <label>Выберите функцию для заполнения y</label>
        <select v-model.number='fun'>
          <option value='0' selected>sin x</option>
          <option value='1'>e^x</option>
          <option value='2'>x^2</option>
        </select>
      </fieldset>
      <fieldset>
        <label>Число узлов интерполяции</label>
        <input type='number' v-model.number='nodes_number' min='1' />
      </fieldset>
      <fieldset>
        <label>Значения x</label>
        <ul>
          <li v-for='x, idx in X' :key='idx'><input type='text' v-model.number='X[ idx ]' /></li>
        </ul>
      </fieldset>
      <fieldset>
        <label>Значения y</label>
        <ul>
          <li v-for='y, idx in Y' :key='idx'><input type='text' v-model.number='Y[ idx ]' :disabled='selected == 1' /></li>
        </ul>
      </fieldset>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'InterpolationInput',

    data: function() {
      return {
        selected: '',
        nodes_number: '',
        X: [],
        Y: [],
        fun: -1,
        functions: [
          ( x ) => Math.sin( x ),
          ( x ) => Math.exp( x ),
          ( x ) => x**2,
        ],
      };
    },

    watch: {
      nodes_number: function( ) {
        this.fillX();
        this.fillY();
      },
      selected: function( value ) {
        if ( value == 0 )
          this.fun = -1;
        else if ( this.fun == -1 )
          this.fun = 0;
      },
      X: {
        handler: function( ) {
          this.recalcY();
        },
        deep: true,
      },
      fun: function() {
        this.recalcY();
      },
    },

    methods: {
      fillX: function() {
        if ( this.X.length <= this.nodes_number )
          for ( let i = 0; i < this.nodes_number - this.X.length; ++i )
            this.X.push( 0.0 );

        if ( this.X.length > this.nodes_number )
          for ( let i = 0; i < this.X.length - this.nodes_number; ++i )
            this.X.pop(); 
      },
      fillY: function() {
        if ( this.Y.length <= this.nodes_number )
          for ( let i = 0; i < this.nodes_number - this.Y.length; ++i )
            this.Y.push( 0.0 );

        if ( this.Y.length > this.nodes_number )
          for ( let i = 0; i < this.Y.length - this.nodes_number; ++i )
            this.Y.pop(); 
      },
      recalcY: function() {
        for ( let i = 0; i < this.Y.length; ++i )
            this.Y[ i ] = ( this.selected == 1 )? this.functions[ this.fun ]( this.X[ i ] ) : this.Y[ i ];
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>