<template>
 <div class="content">
  <h1>{{Страны}}</h1>
  <h2 class="col-12">{{title}}</h2>
  <p class="col-12">{{note}} </p>
  <div class="row fotoBlog">
    <div class="col-md-6 col-lg-4" v-for="(data,index) in products" :key="index">
      <img :src="data.image" class="img-fluid">


      <h3><router-link  :to=data.country>{{data.productTitle}}</router-link></h3>
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
      title: 'Города и страны, где я путешествовал',
      note: 'кликайте по названию и переходите на другую страницу',
      products: [{
          productTitle: "Китай",
          image: require('./fotoChina/chinaGeneral.jpg'),
          country: '/china',
          productId: 1
        },
        {
          productTitle: "Вьетнам",
          image: require('./fotoVetnam/vtm10.jpg'),
          country:'/vietnam',
          productId: 2
        },
        {
          productTitle: "Испания",
          image: require('./fotoBars/bars3.jpg'),
          country:'/spain',
          productId: 3
        },
        {
          productTitle:"Майорка",
          image : require('./fotoMajorca/maj5.jpg'),
          country:'/majorca',
          productId:7
        },
        {
          productTitle:"Ибица",
          image : require('./fotoIbiza/ibz1.jpg'),
          country:'/ibiza',
          productId:8
        },
        {
          productTitle: "ОАЭ",
          image: require('./fotoDubay/db1.jpg'),
          country:'/uae',
          productId: 4
        },
        {
          productTitle: "Египит",
          image: require('./fotoEgipt/egp8.jpg'),
          country:'/egypt',
          productId: 5
        },
        {
          productTitle: "Израиль",
          image: require('./fotoEzrail/izr2.jpg'),
          country:'/israel',
          productId: 6
        },
        {
          productTitle: "Греция",
          image: require('./fotoGrc/grc4.jpg'),
          country: '/greece',
          productId: 7
        }
      ]
    }
  },
 methods:{
 goTodetail(prodId) {
   this.$router.push({name:'details',params:{Pid:prodId}})
 }
},
}
</script>
<style scoped>
.content{
  padding-top: 50px;
}
.fotoBlog{
 overflow: hidden;
 max-width: 1140px;
}
.fotoBlog img{
  width: 390px;
  height: 300px;
  object-fit: cover;
}
</style>
