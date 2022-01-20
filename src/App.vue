<template>
  <div id="app">
    <Header
    @searchFilms="getFilms($event)" @searchSeries="getSeries($event)"
    />
    <Main 
    :filmList="filmsArray"
    :seriesList="seriesArray"
    />
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
          filmsArray: [],
          seriesArray: [],   
  }
},
methods: {
  getFilms(value){
    this.filmsArray = value;
  },
  getSeries(value){
    this.seriesArray = value;
  }
}
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import '~mdb-ui-kit/css/mdb.min.css';
</style>