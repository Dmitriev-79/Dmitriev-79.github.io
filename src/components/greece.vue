<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <p>
        Греция&nbsp;&mdash; страна на&nbsp;юге Европы, расположенная на&nbsp;самой южной оконечности Балканского полуострова, с&nbsp;протяженными побережьями и&nbsp;островами в&nbsp;Эгейском, Ионическом, Критском и&nbsp;Средиземном морях.
У&nbsp;страны древняя культура, которая оказала значительное влияние на&nbsp;искусство, язык, философию, политику и&nbsp;спорт западного общества. Огромное число явлений западной культуры зародилось именно в&nbsp;Древней Греции&nbsp;&mdash; это театр, философия как таковая, демократическая модель государственного устройства, олимпийское движение.
      </p>
      <h2>{{title1}}</h2>
      <p>
        Афины&nbsp;&mdash; античная колыбель величайшей цивилизации и&nbsp;столица солнечной Греции.
         Найти в&nbsp;Европе город хотя&nbsp;бы отдаленно напоминающий Афины&nbsp;&mdash; невозможно. Этот старинный город пережил рассвет еще два с&nbsp;половиной тысячелетия назад.
        Я&nbsp;думаю любому из&nbsp;Вас необходимо там побывать, именно в&nbsp;этом городе одна из&nbsp;старых историй, вплоть до&nbsp;5&nbsp;века до&nbsp;нашей эры.
      </p>
      <h2>Что там видел интересного:</h2>
      <ul>
        <li>Ходил на экскурсию в 6 утра. Именно в это время солнце не так сильно жарит, и можно спокойно погулять по Акрополю.</li>
        <li>Видел самую веселую армию. Мужики в юбках, с бубенцами на туфлях.</li>
        <li>Видел единственный уцелевший щит спартанца, который весит 20 кг. Спартанец не имел право его класть,  обязан всегда носить  на руке.</li>
        <li>В Греции ничего не знают о существовании "Греческого салата".</li>
      </ul>
    </main>
    <div class="row content">
      <div class="col-lg-6">
        <div v-if='showPreloded'  class="preloader">
          <svg  class="preloader__image" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
            <path fill="currentColor"
            d="M304 48c0 26.51-21.49 48-48 48s-48-21.49-48-48 21.49-48 48-48 48 21.49 48 48zm-48 368c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.49-48-48-48zm208-208c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.49-48-48-48zM96 256c0-26.51-21.49-48-48-48S0 229.49 0 256s21.49 48 48 48 48-21.49 48-48zm12.922 99.078c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48c0-26.509-21.491-48-48-48zm294.156 0c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48c0-26.509-21.49-48-48-48zM108.922 60.922c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.491-48-48-48z">
          </path>
        </svg>
      </div>
      <div v-if='show'>
        <h2>Погода в {{title2}}:</h2>
        <div><span class="fat">Общее описание:</span> {{todos.weather[0].description}}</div>
        <div><span class="fat">Облачночть:</span> {{todos.clouds.all}}%</div>
        <div><span class="fat"> Температура:</span> {{todos.main.temp}} С&deg;</div>
        <div><span class="fat"> Ощущается как:</span> {{todos.main.feels_like}} С&deg;</div>
        <div><span class="fat"> Скорость ветра:</span> {{todos.wind.speed}} м/сек</div>
      </div>
      <div v-else>
        <h2 >Погода:</h2>
        <input v-if="showBtn"  class="btn btn-primary" type="submit" v-on:click='funcshow' value="запросить свежие данные">

      </div>
    </div>
    <div class="col-lg-6">
      <h2>Местоположение {{title1}}</h2>
      <div id='map' class="map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d100621.22936695188!2d23.66829933952863!3d37.990816432734675!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x14a1bd1f067043f1%3A0x2736354576668ddd!2z0JDRhNC40L3Riywg0JPRgNC10YbQuNGP!5e0!3m2!1sru!2sru!4v1578243418518!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen></iframe>
      </div>
    </div>
  </div>

  <div class="content">
    <h2>Мои фотографии в&nbsp;самых интересных местах, где я&nbsp;успел побывать</h2>
    <div class="row fotoBlog">
      <div class="col-xs-12 col-sm-6 col-lg-4" v-for="(data,index) in products" :key="index">
      <a data-fancybox :src="data.image" >  <img :src="data.image" class="img-fluid"></a>
        <p class="content__title">{{data.productTitle}}</p>
      </div>
    </div>
  </div>
  <app-footer></app-footer>
</div>
</template>
<script>
import Footer from './footer.vue'
export default{
  components:{
    'app-footer': Footer
  },
  name:'blog',
  data() {
    return {
      todos: '',
      title: 'Греция',
      title1: 'Афины',
      title2: 'Афинах',
      show: false,
      showPreloded: false,
      showBtn: true,
      products: [

      {
        productTitle: "В афинском Акрополе Дом или Храм Ники",
        image: require('./fotoGrc/grc3.jpg'),

        productId: 3
      },
      {
        productTitle:"Акрополь",
        image : require('./fotoGrc/grc4.jpg'),

        productId:7
      },
      {
        productTitle:"На заднем фоне Храм, который разнесли взрывом, а потом восстановили по кусочкам",
        image : require('./fotoGrc/grc5.jpg'),
        productId:8
      },
      {
        productTitle: "Единственный уцелевший щит спартанца. Весит 20 кг",
        image: require('./fotoGrc/grc6.jpg'),
        productId: 4
      },
      {
        productTitle: "Сижу на месте первого в мире банка. Судя по руинам он обанкротился",
        image: require('./fotoGrc/grc7.jpg'),
        productId: 5
      },
      {
        productTitle: "На этом месте родилась фраза 'Инициатива наказуема' ",
        image: require('./fotoGrc/grc8.jpg'),
        productId: 6
      },
      {
        productTitle: "Храм Гефеста",
        image: require('./fotoGrc/grc9.jpg'),
        productId: 6
      },
      {
        productTitle: "Греческая армия в юбках и с бубенчиками на туфлях",
        image: require('./fotoGrc/grc11.jpg'),
        productId: 6
      }
    ]
  }
},
methods:{
  goTodetail(prodId) {
    this.$router.push({name:'details',params:{Pid:prodId}})
  },
  loader(){
    this.showPreloded = !this.showPreloded

  },
  funcshow(e){
    this.showPreloded = true;
    this.showBtn = false;
    setTimeout(this.weatherApi, 100)
  },
  weatherApi(){

    try{
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Athens&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
      .then(response => response.json())
      .then(json => {
        this.todos=json
        this.show = !this.show
        this.showPreloded = false
      })
    }catch(e){
      alert(e)
    }
  },


  onloading(){

  }
},

mounted(){

}
}
</script>
<style scoped>
.content{
  text-align: left;
  padding-top: 100px;
}
main{
  text-align: left;
  padding-top: 50px;
}
.fat{
  font-weight: 600;
}
.fotoBlog{
  overflow: hidden;
  max-width: 1140px;
}
.content__title{
  padding-bottom: 40px;
}
.fotoBlog img{
  width: 100%;
  height: 90%;
  object-fit: cover;

}
h3 {
  font-size: 1rem;
  font-weight: 600;
}
p{
  font-size: 14px;
}
.btn-primary{
  margin-top: 20px;
  margin-bottom: 20px;
}
.preloader {
  position: absolute;
  left: 0;
  top: 4px;
  right: 0;
  bottom: 0;
  overflow: hidden;
  /* фоновый цвет */
  z-index: 1001;
}

.preloader__image {
  position: relative;
  top: 50%;
  left: 50%;
  width: 70px;
  height: 70px;
  margin-top: -35px;
  margin-left: -35px;
  text-align: center;
  animation: preloader-rotate 2s infinite linear;
}
@keyframes preloader-rotate {
  100% {
    transform: rotate(360deg);
  }
}

.loaded_hiding .preloader {
  transition: 0.3s opacity;
  opacity: 0;
  display: block;
}

.loaded .preloader {
  display: none;
}
</style>
