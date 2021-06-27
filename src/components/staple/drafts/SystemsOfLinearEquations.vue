<template>
  <div class='system-of-linear-equations'>
    <h2>Решение систем линейных алгебраических уравнений ( СЛАУ )</h2>
    <form>
      <label>Метод</label>
      <select name='method'>
        <option disabled>Выберите метод решения</option>
        <option>Метод Гаусса</option>
        <option>Метод Гаусса с выбором главного элемента по строкам</option>
        <option>Метод Гаусса с выбором главного элемента по столбцам</option>
        <option>Метод простых итераций</option>
        <option>Метод Гаусса-Зейделя</option>
      </select>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'SystemsOfLinearEquations',
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
