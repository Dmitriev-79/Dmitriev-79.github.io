<template>
  <div class="home">
    <app-carusel></app-carusel>
    <div class="content">
      <div class="block">
        <h1>{{title}}</h1>

        <p class="items">
          <img class="logo" src="../img/logo.png" alt="Самолет">
          Этот сайт создан для того, чтобы запомнить те&nbsp;места, где я&nbsp;побывал
          и&nbsp;поделиться своими впечатлениями с&nbsp;теми, кто туда собирается.
          Для просмотра страниц перейдите на&nbsp;вкладку &laquo;страны&raquo; и&nbsp;гуляйте по&nbsp;городам и&nbsp;странам,
          кликая по&nbsp;их&nbsp;названиям. На&nbsp;страницах указана погода в&nbsp;реальном времени на&nbsp;текущий день,
          это поможет вам понять, стоит&nbsp;ли сейчас туда собираться. Если у&nbsp;вас возникли вопросы, постараюсь вам на&nbsp;них ответить.
          Для этого перейдите на&nbsp;вкладку &laquo;контакты&raquo; и&nbsp;напишите мне письмо.

        </p>
      </div>
      <figure>
        <div class="fixed-wrap">
          <div id="fixed">

          </div>
        </div>
      </figure>
      <div class="container-fluid">
        <div class="row jumbotron">
          <div class="col-xs-12 col-sm-12 col-md-9 col-lg-9 col-xl-10">
            <p class="lead">
              Поедем, я&nbsp;готов; куда&nbsp;бы вы, друзья,<br>
              Куда&nbsp;б ни&nbsp;вздумали, готов за&nbsp;вами я<br>
              Повсюду следовать, надменной убегая:<br>
              К&nbsp;подножию&nbsp;ль стены далекого Китая,<br>
              В&nbsp;кипящий&nbsp;ли Париж, туда&nbsp;ли наконец,<br>
              Где Тасса не&nbsp;поет уже ночной гребец,<br>
              Где древних городов под пеплом дремлют мощи,<br>
              Где кипарисные благоухают рощи,<br>
              Повсюду я&nbsp;готов  ...<br>
             <strong>   А.С. Пушкин</strong>
            </p>
          </div>
          <div class="col-xs-12 col-sm-12 col-md-9 col-lg-9 col-xl-10">
            <img class="img-lead" src="../img/img10.jpg" alt="Венеция">
          </div>
        </div>
      </div>
    </div>
    <app-footer></app-footer>
  </div>
</template>
<script>
import Carusel from './carusel.vue'
import Footer from './footer.vue'
export default {
  components:{
    'app-carusel': Carusel,
    'app-footer': Footer
  },
  name: 'на главную',
  data () {
    return {
      title: 'Дорогой друг!',

    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content{
  padding-top: 50px;
}
.items{
  line-height: 41px;
  font-size: 24px;
  text-align: left;
  position: relative;
}
.block{
  max-width: 83%;
  border: 1px solid #027CFF;
  padding: 30px;
  color: #014288;
  margin-bottom: 30px;
}
.img-lead{
width: 100%;
}
.jumbotron {
  padding: 1em;
  border-radius: 0;
  width: 70%;
  margin: 0 auto;
  margin-top: 20px;
}
.lead {
  font-size: 1.25rem;
  font-weight: 300;
  text-align: left;
}
.logo{
  max-width: 20vw;
  position: absolute;
  left: 60vw;
  top: -2vw;
}
#fixed {
  height: 400px;
  border-top: 4px solid #f0f0f0;
  border-bottom: 4px solid #f0f0f0;
  background: url(../img/img8.jpg) no-repeat center center fixed;
  background-blend-mode: multiply;
  background-color: lightblue;
  background-size: cover;
  -o-background-size: cover;
  -moz-background-size: cover;
  -webkit-background-size: cover;
}
</style>
