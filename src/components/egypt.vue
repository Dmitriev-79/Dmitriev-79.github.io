<template>
  <div>
    <h2>{{title}}</h2>
    <main>
      <p>
        Египет&nbsp;&mdash; страна в&nbsp;северо-восточной части Африки со&nbsp;столицей в&nbsp;Каире&nbsp;&mdash; крупнейшем городе всего Африканского континента. Египет занимает и&nbsp;небольшую часть Азии, простираясь на&nbsp;Синайский полуостров. На&nbsp;юге граничит с&nbsp;Суданом, на&nbsp;западе&nbsp;&mdash; с&nbsp;Ливией, на&nbsp;северо-востоке&nbsp;&mdash; с&nbsp;Израилем и&nbsp;сектором Газа. Ближайшими восточными соседями являются также Иордания и&nbsp;Саудовская Аравия, находящиеся на&nbsp;противоположном берегу Красного моря. Средиземное и&nbsp;Красное моря определяют соответственно северную и&nbsp;восточную границы Египта, а&nbsp;его
        главной природной доминантой является протекающий через всю страну Нил, создающий увлажненной плодородной долиной, пригодную для проживания и&nbsp;земледелия.
        История Египта насчитывает 5&nbsp;тысячелетий, за&nbsp;которые на&nbsp;этой территории успело расцвести и&nbsp;увянуть после завоевания Александра Македонского легендарное египетское царство, после чего в&nbsp;истории страны начался эллинистический, а&nbsp;затем и&nbsp;римский период. В&nbsp;первой половине&nbsp;I тысячелетия Египет был христианской территорией, входившей в&nbsp;состав Византии, однако после прихода арабских завоевателей в&nbsp;VII века стал доминировать ислам.
      </p>
      <h2>{{title1}}</h2>
      <p>
        Каир&nbsp;&mdash; столица Египта. Поэтическое прозвище: &laquo;город тысячи минаретов&raquo;. Сами каирцы чаще называют свой город &laquo;Маср&raquo; (مصر‎ араб.), т.е. &laquo;Египет&raquo;. Главной достопримечательностью Каира, находящейся на&nbsp;его западной окраине, является долина Гизы, где можно увидеть пирамиды Хеопса, Хефрена и&nbsp;Микерина, являющиеся символом Египта. Прикоснуться к&nbsp;древнейшей истории и&nbsp;посмотреть на&nbsp;жуткие мумии можно в&nbsp;Каирском египетском музее, на&nbsp;осмотр экспозиций которого может уйти целый день. Много в&nbsp;Каире и&nbsp;мечетей, самыми популярными у&nbsp;туристов являются мечети Аль-Азхар, у&nbsp;рынка, а&nbsp;также мечеть султана Хасана.
      </p>
      <h2>Что там видел интересного:</h2>
      <ul>
        <li>Самая важная достопримечательность  это Красное море и кораллы.</li>
        <li>Очень большую мечеть Аль-Азхар.</li>
        <li>Пирамиды в Гизе.</li>
        <li>Соженный после революции Дом правительства.</li>

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
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d55251.37709964616!2d31.223444832512136!3d30.05948381032293!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x14583fa60b21beeb%3A0x79dfb296e8423bba!2z0JrQsNC40YAsINCt0LvRjC3QmtCw0YXQuNGA0LAsINCV0LPQuNC_0LXRgg!5e0!3m2!1sru!2sru!4v1578478294327!5m2!1sru!2sru" width="100%" height="230" frameborder="0" style="border:0;" allowfullscreen=""></iframe>
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
      title: 'Египит',
      title1: 'Каир',
      title2: 'Каире',
        title3: 'Каира',
      show: false,
      showPreloded: false,
      showBtn: true,
      products: [{
        productTitle: "Бидуинская деревушка в пустыни",
        image: require('./fotoEgipt/egp1.jpg'),

        productId: 1
      },
      {
        productTitle: "Мечеть Аль-Азхар",
        image: require('./fotoEgipt/egp3.jpg'),

        productId: 3
      },
      {
        productTitle:"Каир с высоты мечети Аль-Азхар",
        image : require('./fotoEgipt/egp4.jpg'),

        productId:7
      },
      {
        productTitle:"Сожженый дом правительства после революции 2011 года ",
        image : require('./fotoEgipt/egp5.jpg'),
        productId:8
      },
      {
        productTitle:"Ежи на которых ступала моя нога",
        image : require('./fotoEgipt/egp6.jpg'),
        productId:8
      },
      {
        productTitle:"Пирамиды Гизе",
        image : require('./fotoEgipt/egp7.jpg'),
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
    fetch('https://api.openweathermap.org/data/2.5/weather?q=Cairo&units=metric&appid=bd4c2b86768f3ebeb5eb2997f0ca09c5&lang=ru')
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
