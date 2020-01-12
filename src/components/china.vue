<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <h2>Остров Хайнянь</h2>
      <p>Остров Хайнань часто называют &laquo;Восточными Гавайями&raquo; из-за его расположения на&nbsp;одной широте с&nbsp;Гавайскими островами. Остров омывается водами Южно-Китайского моря, более 300 дней в&nbsp;году стоит ясная солнечная погода. Количество осадков в&nbsp;год&nbsp;&mdash; 1500&nbsp;мм. Xайнань&nbsp;&mdash; второй по&nbsp;величине (после Тайваня) и&nbsp;единственный в&nbsp;Китае остров с&nbsp;тропическим климатом. На&nbsp;острове Xайнань чистый и&nbsp;целебный воздух. Кстати, парк Наньшань, расположенный на&nbsp;острове,&nbsp;&mdash; это единственное в&nbsp;мире место, соответствующее международным экологическим стандартам&nbsp;&mdash; ISO 14000.

        Среднегодовая температура воздуха составляет + 24&deg;С, воды&nbsp;&mdash; + 26&nbsp;&deg;C.&nbsp;Средняя температура на&nbsp;острове Хайнань в&nbsp;январе&nbsp;&mdash; около +22&deg;С.&nbsp;Самые жаркие месяцы&nbsp;&mdash; июль и&nbsp;август, когда среднемесячная температура достигает 29&deg;С тепла, поэтому постарайтесь избежать посещения острова в&nbsp;самый разгар лета. Золотой сезон на&nbsp;Хайнане&nbsp;&mdash; с&nbsp;ноября по&nbsp;май. Регион традиционно считается &laquo;коридором тайфунов&raquo;, поэтому остров&nbsp;&mdash; рай для любителей виндсерфинга.
      </p>
      <h2>Санья</h2>
      <p>
        Санья&nbsp;&mdash; город на&nbsp;южной оконечности китайского острова Хайнань, который славится своими заливами и&nbsp;большим количеством морских курортов. На&nbsp;берегу залива Ялунвань открыто несколько роскошных гостиниц. Остров Учжичжоу с&nbsp;его коралловыми рифами популярен у&nbsp;любителей подводного плавания, серфинга и&nbsp;других водных видов спорта. На&nbsp;небольшом искусственном острове, расположенном на&nbsp;территории огромного храмового комплекса Наньшань, возвышается бронзовая статуя богини Гуаньинь высотой 108&nbsp;метров. Вот туда я и отправился в своем путешествии.
      </p>
      <h2>Что я там делал в первый раз:</h2>
      <ul>
        <li>Путешествовал за 60 км от отеля, не зная  китайский и английский. Китайцы каким-то чудом вас понимают.</li>
        <li>Гонял крабов по ночному берегу моря. Их там навалом.</li>
        <li> Ел очень вкусные манго большие и маленькие.</li>
        <li>Ездил  на электрической велорикше по встречке. У них там это в порядке вещей.</li>
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
      <h2>Местоположение {{title1}}</h2>
      <div id='map' class="map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1931493.04863949!2d108.37939437442152!3d18.999998876406405!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x314fd93fac0cc9af%3A0x15ec8f416c59a78!2sHainan%20Dao!5e0!3m2!1sru!2sru!4v1577786656580!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen></iframe>
      </div>
    </div>
  </div>

    <div class="content">
      <h2>Мои фотографии в&nbsp;самых интересных местах, где я&nbsp;успел побывать</h2>
      <div class="row fotoBlog">
        <div class="col-xs-12 col-sm-6 col-lg-4" v-for="(data,index) in products" :key="index">
          <img :src="data.image" class="img-fluid">
          <p>{{data.productTitle}}</p>
        </div>
      </div>
    </div>
 <app-footer></app-footer>
  </div>
</template>
<script>
import Footer from './footer.vue'
export default{
  name:'china',
  components:{
    'app-footer': Footer
  },
  data() {
    return {
      todos: '',
      title: 'Китай',
      title2: 'Хайнянь',
      show: false,
      showPreloded: false,
      showBtn: true,
      products: [{
        productTitle: "Принцесса Гуаньинь",
        image: require('./fotoChina/china1.jpg'),
        productId: 1
      },
      {
        productTitle: "В Китае все Ок",
        image: require('./fotoChina/china3.jpg'),

        productId: 3
      },
      {
        productTitle:"Внутри храма принцессы Гуаньинь",
        image : require('./fotoChina/china4.jpg'),

        productId:7
      },
      {
        productTitle:"Весь храм из золота",
        image : require('./fotoChina/china6.jpg'),
        productId:8
      },

      {
        productTitle: "Урны с прахом монахов",
        image: require('./fotoChina/china8.jpg'),
        productId: 5
      },
      {
        productTitle: "Все стены заставлены прахом",
        image: require('./fotoChina/china9.jpg'),
        productId: 6
      },

      {
        productTitle: "На пороге храма Шау-линь",
        image: require('./fotoChina/china11.jpg'),
        productId: 8
      },
      {
        productTitle: "Вид с птичьего полета",
        image: require('./fotoChina/china18.jpg'),
        productId: 14
      },
      {
        productTitle: "Вид города с моря",
        image: require('./fotoChina/china19.jpg'),
        productId: 14
      }
    ]
  }
},
methods:{
  goTodetail(prodId) {
    this.$router.push({name:'details',params:{Pid:prodId}})
  },
  funcshow(e){
    this.showPreloded = true;
    this.showBtn = false;

  setTimeout(this.weatherApi, 100)

  },
  weatherApi(){
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Sanya&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
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
.fotoBlog img{
  width: 100%;
  height: 90%;
  object-fit: cover;
  margin-bottom: 10px;
}
h3 {
    font-size: 1rem;
    font-weight: 600;
}
p{
  font-size: 1rem;
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
