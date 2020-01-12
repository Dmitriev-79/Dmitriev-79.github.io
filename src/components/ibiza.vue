<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <p>Испания является одной из&nbsp;самых красивых и&nbsp;манящих стран в&nbsp;мире. Наверное почти у&nbsp;всех она ассоциируется в&nbsp;первую очередь с&nbsp;солнечными пляжами и&nbsp;теплым-теплым морем.Это родина паэльи, корриды, кастаньетов и&nbsp;фламенко. Страна со&nbsp;своей богатой историей и&nbsp;культурой, на&nbsp;протяжении многих тысячелетий является одним из&nbsp;культурных центов Европы. Испания сама по&nbsp;себе является особенной страной, обобщить ее&nbsp;как географически, так и&nbsp;культурно становится невыполнимой задачей. Миллионы людей посещают Испанию и&nbsp;нередко побывав тут один раз, они возвращаются снова.
      </p>
      <h2>{{title1}}</h2>
      <p>
      Ибица&nbsp;&mdash; самый модный курорт Европы.
      Солнце, море, свобода, круглосуточное веселье, переходящее в&nbsp;&laquo;отрыв&raquo;. Здесь самое большое колличество красивых пляжей с&nbsp;голубыми флагами.
      Отдыхает в&nbsp;основном европейская и&nbsp;амереканская молодежь. Ибица никогда не&nbsp;спит. Как расказывали местные, некоторые молодые туристы так и&nbsp;не&nbsp;доезжают до&nbsp;своих отелей, так как тусят круглосуточно, ночью в&nbsp;клубе, а&nbsp;днем на&nbsp;пляже.
      </p>
      <h2>Что там видел интересного:</h2>
      <ul>
        <li>Очень красивые пляжи.</li>
        <li>Яхту Абрамовича.</li>
        <li>Свободную от предрассудков молодёжь.</li>
        <li>Большое колличество клубов.</li>
        <li>Хочется бросить все и остаться там жить.</li>
        <li>Кто-то на остров приехал на Ладе Нива</li>

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
      <h2>Местоположение острова {{title1}}</h2>
      <div id='map' class="map">

        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d397031.6704189466!2d1.1372024189236658!3d38.97400796049512!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1299476385093943%3A0x9064725cd8426d6!2z0JjQstC40YHQsA!5e0!3m2!1sru!2sru!4v1578395072027!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen></iframe>
      </div>
    </div>
  </div>

  <div class="content">
    <h2>Мои фотографии в&nbsp;самых интересных местах, где я&nbsp;успел побывать</h2>
    <div class="row fotoBlog">
      <div class="bottom col-xs-12 col-sm-6 col-lg-4" v-for="(data,index) in products" :key="index">
        <a data-fancybox :src="data.image" >  <img :src="data.image" class="img-fluid"></a>
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
      title: 'Испания',
      title1: 'Ибица',
      title2: 'Ибице',
      show: false,
      showPreloded: false,
      showBtn: true,
      products: [{
        productTitle: "Самый красивый и чистый пляж на Ибице",
        image: require('./fotoIbiza/ibz1.jpg'),

        productId: 1
      },
      {
        productTitle: "На фоне, красивого и чистого пляжа",
        image: require('./fotoIbiza/ibz2.jpg'),

        productId: 2
      },
      {
        productTitle: "Купаясь на пляже,  видел дно моря на глубене 10 метров",
        image: require('./fotoIbiza/ibz3.jpg'),

        productId: 3
      },
      {
        productTitle:"Какой-то знаменитый храм",
        image : require('./fotoIbiza/ibz4.jpg'),

        productId:7
      },
      {
        productTitle:"Вид с площадки этого храма, на остров Ибица",
        image : require('./fotoIbiza/ibz5.jpg'),
        productId:8
      },
      {
        productTitle:"Неожиданно на Ибице встретил нашу советскую Ниву",
        image : require('./fotoIbiza/ibz6.jpg'),
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
    fetch('https://api.openweathermap.org/data/2.5/weather?q=Ibiza&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
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
  padding-bottom: 60px;

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
