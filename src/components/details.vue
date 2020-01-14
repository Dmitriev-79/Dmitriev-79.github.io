<template>
  <div class="details">
    <div class="container">
      <div class="row">
        <div class="col-md-12" v-for="(product, index) in products" :key="index">
          <div v-if="proId == product.productId">
            <h1>{{product.productTitle}}</h1>
            <img :src="product.image" class="img-fluid">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default{
  name: 'details',
  data () {
    return {
      proId: this.$route.params.Pid,
      title: 'details',
      products: [
        {
          productTitle: 'Китай',
          image: require('../img/img4.jpg'),
          productId: 1
        },
        {
          productTitle: 'Вьетнам',
          image: require('../img/img4.jpg'),
          productId: 2
        },
        {
          productTitle: 'Испания',
          image: require('../img/img4.jpg'),
          productId: 3
        },
        {
          productTitle: 'ОАЭ',
          image: require('../img/img4.jpg'),
          productId: 4
        },
        {
          productTitle: 'Египит',
          image: require('../img/img4.jpg'),
          productId: 5
        },
        {
          productTitle: 'Израиль',
          image: require('../img/img4.jpg'),
          productId: 6
        },
        {
          productTitle: 'Майорка',
          image: require('../img/img4.jpg'),
          productId: 7
        },
        {
          productTitle: 'Ибица',
          image: require('../img/img4.jpg'),
          productId: 8
        }

      ]
    }
  }
}
</script>
