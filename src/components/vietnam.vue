<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <p>
        Вьетнам&nbsp;&mdash; это страна вечного лета.
        Роскошные километровые пляжи, кристально чистый океан и&nbsp;живописные скалы&nbsp;&mdash; типичный пейзаж Вьетнама.
        В&nbsp;местных ресторанах можно отведать свежие&nbsp;и, при этом очень дешевые морепродукты.
      </p>
      <h2>{{title1}}</h2>
      <p>
        Муйне&nbsp;&mdash; один из&nbsp;лучших пляжных курортов Вьетнама. Иногда его называют пригородом крупного города Фантьета, а&nbsp;иногда путают с&nbsp;прибрежной рыбацкой деревушкой.
        На&nbsp;самом деле курорт Муйне не&nbsp;город и&nbsp;не&nbsp;поселок, а&nbsp;застроенная современными отелями туристическая зона на&nbsp;берегу одноименного залива.
        Здесь практически не&nbsp;ощущается языковой барьер: на&nbsp;курорте не&nbsp;проблема найти русскоговорящего гида, вывески на&nbsp;улицах и&nbsp;меню в&nbsp;ресторанах, как правило, дублируются на&nbsp;русском.
        Жизнь на&nbsp;побережье течет размеренно. В&nbsp;курортной зоне нет ночных клубов и&nbsp;дискотек, нет и&nbsp;достопримечательностей, которые собирают вокруг себя толпы туристов. Зато Муйне&nbsp;&mdash; превосходное место для занятий водными видами спорта, сюда съезжаются любители кайтсерфинга и&nbsp;виндсерфинга.
      </p>
      <h2>Что я там делал в первый раз:</h2>
      <ul>
        <li>Кормил крокодилов</li>
        <li>Ел крокодилов</li>
        <li>Кормил страусов</li>
        <li>Отведал струсиного супа</li>
        <li>Ночью гонял по номеру гекона</li>
        <li>Поймал на удочку пиранью</li>
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
        <h2>Погода в {{title1}}:</h2>
        <div><span class="fat">Общее описание:</span> {{todos.weather[0].description}}</div>
        <div><span class="fat">Облачночть:</span> {{todos.clouds.all}}%</div>
        <div><span class="fat"> Температура:</span> {{todos.main.temp}} С&deg;</div>
        <div><span class="fat"> Ощущается как:</span> {{todos.main.feels_like}} С&deg;</div>
        <div><span class="fat"> Скорость ветра:</span> {{todos.wind.speed}} м/сек</div>
      </div>
      <div v-else>
        <h2 >Погода:</h2>
        <input v-if='showBtn'  class="btn btn-primary" type="submit" v-on:click='funcshow' value="запросить свежие данные">

      </div>
    </div>
    <div class="col-lg-6">
      <h2>Местоположение {{title1}}</h2>
      <div id='map' class="map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d250690.48731589506!2d108.17069289727802!3d10.960436902311532!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31768e4c7f7c96b5%3A0x1a406b72c1020724!2z0JzRg9C50L3QtSwg0KTQsNC90YLRhdGM0LXRgiwg0JHQuNC9INCi0YPQsNC9LCDQktGM0LXRgtC90LDQvA!5e0!3m2!1sru!2sru!4v1577969628632!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen=""></iframe>

      </div>
    </div>
    <app-footer></app-footer>
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
</div>
</template>
<script>
import Footer from './footer.vue'
export default{
  components:{
    'app-footer': Footer
  },
  name:'vietnam',
  data() {
    return {
      todos: '',
      title: 'Въетнам',
      title1: 'Муйне',
      show: false,
      showBtn: true,
      showPreloded: false,
      products: [{
        productTitle: "Выбираю ужин",
        image: require('./fotoVetnam/vtm1.jpg'),

        productId: 1
      },
      {
        productTitle: "На рыбалке поймал пиранью",
        image: require('./fotoVetnam/vtm2.jpg'),

        productId: 2
      },
      {
        productTitle: "Пешком домой",
        image: require('./fotoVetnam/vtm3.jpg'),

        productId: 3
      },
      {
        productTitle:"Во вьетнаме есть ледяной бар",
        image : require('./fotoVetnam/vtm4.jpg'),

        productId:7
      },
      {
        productTitle:"За ледяным столом",
        image : require('./fotoVetnam/vtm5.jpg'),
        productId:8
      },
      {
        productTitle: "Акула на ужин",
        image: require('./fotoVetnam/vtm6.jpg'),
        productId: 4
      },
      {
        productTitle: "Готовлю крокодила",
        image: require('./fotoVetnam/vtm7.jpg'),
        productId: 5
      },
      {
        productTitle: "Лобстер",
        image: require('./fotoVetnam/vtm8.jpg'),
        productId: 6
      },
      {
        productTitle: "Пляж",
        image: require('./fotoVetnam/vtm9.jpg'),
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
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Saint-Laurent-du-Maroni&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
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

},

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
  padding-bottom: 30px;
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
  font-size: 18px;
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
