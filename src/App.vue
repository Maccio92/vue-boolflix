<template>
  <div id="app">
    <Header
    @search="getFilms($event)"
  />
    <Main />
    <Footer />
  </div>
</template>

<script>

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import Footer from "./components/Footer.vue";


export default {
  name: "App",
  components: {
    Header,
    Main,
    Footer,
  },
  data(){
        return{
          filmsArray: null,
          
  }
},
methods: {
  getFilms(array){
    this.filmsArray= array;
  }
}
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>