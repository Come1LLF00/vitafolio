<template>
  <div id='word-cloud' class='wordcloud'>
  </div>
</template>

<script>
  import Anychart from 'anychart'

  export default {
    name:'WordCloud',

    props: {
      Anychart: Object,
    },

    mounted() {
      let _Anychart = this.Anychart || Anychart;
      _Anychart.onDocumentReady(function() {
        var data = [
          { 'x': 'алгоритмы', 'value': 20 },
          { 'x': 'структуры данных', 'value': 30 },
          { 'x': 'PostgreSQL', 'value': 60 },
          { 'x': 'H2', 'value': 50 },
          { 'x': 'Git', 'value': 90 },
          { 'x': 'Subversion', 'value': 75 },
          { 'x': 'Apache Ant', 'value': 80 },
          { 'x': 'Maven', 'value': 65 },
          { 'x': 'Gradle', 'value': 70 },
          { 'x': 'JUnit 4.0', 'value': 40 },
          { 'x': 'Java SE 8', 'value': 98 },
          { 'x': 'C17/C++17', 'value': 55 },
          { 'x': 'Python 3', 'value': 60 },
          { 'x': 'MS Office', 'value': 100 },
          { 'x': 'LaTeX', 'value': 100 },
          { 'x': 'Markdown', 'value': 100 },
          { 'x': 'HTML 5', 'value': 100 },
          { 'x': 'CSS 3', 'value': 100 },
          { 'x': 'JavaScript', 'value': 70 },
          { 'x': 'Linux ( Debian 10 )', 'value': 80 },
          { 'x': 'scilab 5.5.2', 'value': 10 },
          { 'x': 'PHP 8', 'value': 30 },
          { 'x': 'Vue.js 2.x/3.x', 'value': 60 },
          { 'x': 'bash', 'value': 20 },
          { 'x': 'Java EE', 'value': 70 },
          { 'x': 'Spring', 'value': 60 },
        ];
        // create a tag (word) cloud chart
        var chart = _Anychart.tagCloud( data );
        // set a chart title
        chart.title( 'Ключевые навыки' );

        chart.tooltip( false );
        chart.legend( false );
        // set an array of angles at which the words will be laid out
        chart.angles( [ 0, 90, 270 ] )

        // display the word cloud chart
        chart.container( 'word-cloud' );
        chart.draw();
      });
    },
  }
  
</script>

<!-- Add'scoped' attribute to limit CSS to this component only -->
<style scoped>
  .wordcloud {
    height: 400px;
  }
</style>
