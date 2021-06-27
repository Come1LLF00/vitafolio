<template>
  <div class='about'>
    <h2>Ханнанов Ленар Ильнурович</h2>
    <h4>Мужчина, 20 лет, родился 28 октября 2000, не женат</h4>
    <h5>Контакты</h5>
    <ul>
      <li>+7 (927) 933-49-02</li>
      <li>khannanov2000@yandex.ru &mdash; предпочитаемый способ связи</li>
      <li>Октябрьский (Республика Башкортостан), готов к переезду (Санкт-Петербург), не готов к командировкам</li>
      <li>Gitlab с проектами: <a href='https://gitlab.se.ifmo.ru/come_ill_foo'>https://gitlab.se.ifmo.ru/come_ill_foo</a></li>
      <li>Github с проектами: <a href='https://github.com/Come1LLF00'>https://github.com/Come1LLF00</a></li>
    </ul>
    <h3>стажер QA Engineer, стажер-программист, стажер-разработчик ( желательно Java )</h3>
    <dl>
      <dt>Начало карьеры, студенты</dt>
      <dd>&mdash; Информационные технологии, Интернет Мультимедиа</dd>
      <dt>Занятость: стажировка, частичная занятость, проектная работа</dt>
      <dt>График работы: гибкий график, полный день, сменный график, удаленная работа</dt>
    </dl>
    <WordCloud />
    <h3>Обо мне</h3>
    <p>Прохожу обучение в вузе по очной программе бакалавриата</p>
    <h3>Неоконченное высшее образование</h3>
    <dl>
      <dt>2024</dt>
      <dd>
        <strong>Санкт-Петербургский национальный исследовательский университет информационных технологий, механики и оптики, Санкт-Петербург</strong><br>
        ПИИКТ ( Программной Инженерии и Компьютерной Техники ), СППО ( Системное и Прикладное Программное Обеспечение )
      </dd>
    </dl>
    <h3>Знания языков</h3>
    <ul>
      <li>Русский &mdash; родной</li>
      <li>Английский &mdash; B2 &mdash; средне-продвинутый</li>
    </ul>
  </div>
</template>

<script>
  import WordCloud from './about/WordCloud.vue'

  export default {
    name: 'About',
    components: {
      WordCloud
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .about {
    text-align: left;
    padding: 1rem;
  }
</style>
