
<template>
  <div>
    <vue-displacement-slideshow
            :images="images"
            :intensity.number="0.6"
            :speedIn.number="1.4"
            :speedOut.number="0.4"
            ease="Expo.easeInOut"
            ref="slideshow">
          </vue-displacement-slideshow>
        </div>
</template>
<script>
import VueDisplacementSlideshow from "./VueDisplacementSlideshow.vue";

   export default {
       components: {
           VueDisplacementSlideshow,
       },
       computed: {
           images() {
               return [
                   require('../img/img1.jpg'),
                   require('../img/img2.jpg'),
                   require('../img/img3.jpg'),
                   require('../img/img4.jpg'),
                   require('../img/img6.jpg'),
                   require('../img/img7.jpg'),
                   require('../img/img11.jpg'),
                   require('../img/img12.jpg'),
                   require('../img/img13.jpg'),
                   require('../img/img14.jpg'),
                   require('../img/img15.jpg'),
                   require('../img/img16.jpg')
               ];
           }
       },
       methods: {
             init() {
                 //We loop through all our images by calling the 'next' method of our component every 2 seconds
                 setInterval(() => {
                     this.$refs.slideshow.next();
                 }, 1000);
             },
             next(nextImage = null) {
                 if (this.isAnimating) {
                     return;
                 }
                 // Skip animation if the materials are not ready
                 if (this.mat === null) {
                     this.currentImage = mod((this.currentImage + 1), (this.textures.length));
                     return;
                 }
                 this.isAnimating = true;
                 this.nextImage = nextImage !== null ? nextImage : mod((this.currentImage + 1), (this.textures.length));
                 this.assignTexturesToMaterial();
                 this.transitionIn();
                 this.resetValuesAfterAnimation();
             },
         },
       mounted() {
           this.init();
       }
   };
      //Набор картинок

</script>
