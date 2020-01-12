<template>
  <div id="app" class="">
      <!-- navbar -->
      <div class="container2 navbar navbar-expand-lg fixed-top navbar-dark bg-primary">
        <div class="container">

        <router-link to="/" class="navbar-brand">На главную</router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarResponsive">
          <ul class="navbar-nav">
            <li class="nav-item">
            <router-link class="nav-link" to="/services">Страны</router-link>
            </li>
            <li class="nav-item">
             <router-link class="nav-link" to="/contact">Контакты</router-link>
            </li>
          </ul>

        </div>
        </div>
      </div>
      <div class="container">
       <transition name="moveInUp">
         <router-view/>
       </transition>

      </div>

  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container2{
  max-width: 1110px;
  margin: auto;
}
.moveInUp-enter-active{
  animation: fadeIn 0.5s ease-in;
}
@keyframes fadeIn{
  0%{
    opacity: 0;
  }
  50%{
    opacity: 0.5;
  }
  100%{
    opacity: 1;
  }
}
.moveInUp-leave-active{
  animation: moveInUp .3s ease-in;
}
@keyframes moveInUp{
  0%{
    transform: translateY(0);
  }
  100%{
    transform: translateY(-400px);
  }
}
</style>
