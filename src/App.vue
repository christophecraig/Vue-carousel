<template>
  <div id="app">
    <img src="./assets/images/logo.png">
    <hello></hello>
    <carousel>
      <carousel-slide>
    <img src="./assets/images/img1.jpg">
      </carousel-slide>
      <carousel-slide>
    <img src="./assets/images/img2.jpg">
      </carousel-slide>
      <carousel-slide>
    <img src="./assets/images/img3.jpg">
      </carousel-slide>
      <carousel-slide>
    <img src="./assets/images/img4.jpg">
      </carousel-slide>
      <carousel-slide>
    <img src="./assets/images/img5.jpg">
      </carousel-slide>

    </carousel>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Carousel from './components/Carousel'
import CarouselSlide from './components/CarouselSlide'

export default {
  name: 'app',
  components: {
    Hello,
    Carousel,
    CarouselSlide
  }
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
  font-size: 1.6em;
}
</style>
