<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <p>
        Израиль&nbsp;&mdash; страна на&nbsp;Ближнем Востоке у&nbsp;восточного побережья Средиземного моря, которую иудеи, христиане и&nbsp;мусульмане считают библейской Святой Землей. В&nbsp;Старом городе Иерусалима расположены главные святыни страны: Храмовая гора, на&nbsp;которой возведены святилище Купол скалы, древняя Стена Плача и&nbsp;мечеть Аль-Акса, и&nbsp;храм Гроба Господня. Тель-Авив, финансовый центр Израиля, известен своими пляжами, а&nbsp;также зданиями, построенными по&nbsp;проектам архитекторов немецкой школы &laquo;Баухаус&raquo;.
  Севернее лежат город Назарет и&nbsp;пресноводное Тивериадское озеро (Галилейское море), которое в&nbsp;Новом Завете связано со&nbsp;многими событиями из&nbsp;жизни Иисуса Христа. В&nbsp;городе Хайфа у&nbsp;туристов пользуются популярностью гора Кармель, с&nbsp;которой открывается великолепный вид на&nbsp;окрестности, и&nbsp;ухоженные висячие сады. Южнее находятся развалины римского портового города Кесария, основанного царем Иудеи Иродом Великим.
      </p>
      <h2>{{title1}}</h2>
      <p>
        Иерусалим&nbsp;&mdash; священное место для христиан, мусульман и&nbsp;иудеев, объект паломничества верующих со&nbsp;всего мира и&nbsp;просто полный жизни город, самый древний на&nbsp;Ближнем Востоке. На&nbsp;старинных картах именно он&nbsp;изображен в&nbsp;центре мира, именно здесь происходили многие события, описанные в&nbsp;Библии.
      </p>
      <h2>Что там видел интересного:</h2>
      <ul>
        <li>Храм Рождества.</li>
        <li>Храм Гроба Господня.</li>
        <li>Стена Плача. Загадал желание, оно кстати сбылось.</li>
        <li>Побывал в Палестине.</li>
        <li>Плавал в Мертвом море. В нем очень сложно утонуть. Не пытайтесь.</li>
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
        <input v-if='showBtn'  class="btn btn-primary" type="submit" v-on:click='funcshow' value="запросить свежие данные">

      </div>
    </div>
    <div class="col-lg-6">
      <h2>Местоположение {{title3}}</h2>
      <div id='map' class="map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d217027.5412526816!2d35.03527057137286!3d31.796241905783354!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1502d7d634c1fc4b%3A0xd96f623e456ee1cb!2z0JjQtdGA0YPRgdCw0LvQuNC8LCDQmNC30YDQsNC40LvRjA!5e0!3m2!1sru!2sru!4v1578482882400!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen=""></iframe>

      </div>
    </div>
  </div>

  <div class="content">
    <h2>Мои фотографии в&nbsp;самых интересных местах, где я&nbsp;успел побывать</h2>
    <div class="row fotoBlog">
      <div class="bottom col-xs-12 col-sm-6 col-lg-4" v-for="(data,index) in products" :key="index">
          <img :src="data.image" class="img-fluid">
        <div class="content__title">{{data.productTitle}}</div>
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
      title: 'Израиль',
      title1: 'Иерусалим',
      title2: 'Иерусалиме',
        title3: 'Иерусалима',
      show: false,
      showPreloded: false,
      showBtn: true,
      products: [{
        productTitle: "Рано утром при въезде в Иерусалим",
        image: require('./fotoEzrail/izr2.jpg'),

        productId: 1
      },

      {
        productTitle: "У Стены Плача",
        image: require('./fotoEzrail/izr4.jpg'),

        productId: 3
      },

      {
        productTitle:"Рядом со школой Мартина Лютера. Отсюда пошло лютеранство.",
        image : require('./fotoEzrail/izr7.jpg'),
        productId:8
      },
      {
        productTitle:"Табличка Мартина Лютера",
        image : require('./fotoEzrail/izr8.jpg'),
        productId:8
      },
      {
        productTitle:"На площади перед Храмом Гроба Господня",
        image : require('./fotoEzrail/izr9.jpg'),
        productId:8
      },

      {
        productTitle:"Вид внутри Храма",
        image : require('./fotoEzrail/izr11.jpg'),
        productId:8
      },

      {
        productTitle:"Место, где стоял Крест с распятым Иисусом",
        image : require('./fotoEzrail/izr13.jpg'),
        productId:8
      },
      {
        productTitle:"Скала, в которой стоял Крест",
        image : require('./fotoEzrail/izr14.jpg'),
        productId:8
      },
      {
        productTitle:"Распятие в натуральную величину",
        image : require('./fotoEzrail/izr15.jpg'),
        productId:8
      },
      {
        productTitle:"Место под Голгофой, где по приданию захоронен первый человек Адам. Кровь Иисуса стекала с креста по трещине в скале и омывала кости Адама, тем самым смывала грех с рода человеческого.",
        image : require('./fotoEzrail/izr16.jpg'),
        productId:8
      },
      {
        productTitle:"На этом камне Иисуса бальзамировали перед захоронением. Камень насквозь пропитан миром.",
        image : require('./fotoEzrail/izr17.jpg'),
        productId:8
      },

      {
        productTitle:"На месте этого Храма  была пещера, где Иисус воскрес. Каждую Пасху с этого места  ведется прямая трансляция о зажжении священного огня.",
        image : require('./fotoEzrail/izr19.jpg'),
        productId:8
      },

      {
        productTitle:"Эту колонну в одну из Пасх поразила молния.",
        image : require('./fotoEzrail/izr22.jpg'),
        productId:8
      },

      {
        productTitle:"Храм Рождества",
        image : require('./fotoEzrail/izr24.jpg'),
        productId:8
      },
      {
        productTitle:"Там, где звезда, там родился Иисус",
        image : require('./fotoEzrail/izr25.jpg'),
        productId:8
      },
      
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
    fetch('https://api.openweathermap.org/data/2.5/weather?q=Jerusalem&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
    .then(response => response.json())
    .then(json => {
      this.todos=json
      this.show = !this.show
      this.showPreloded = false
    })
    .catch(e=>console.error(e))
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
  padding-bottom: 230px;
  line-height: 15px;

}
.fotoBlog img{
  width: 100%;
  height: 90%;
  object-fit: cover;

}
.bottom{
  padding-bottom: 20px;
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
