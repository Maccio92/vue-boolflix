<template>
  <div class="bg-dark" id="app">
    <Header
    @searchFilms="getFilms($event)" 
    @searchSeries="getSeries($event)"
    @showFilm="showingListFilms($event)"
    @showSeries="showingListSeries($event)"
    />
    <Main 
    :filmList="filmsArray"
    :seriesList="seriesArray"
    :showingFilm ="showListFilms"
    :showingSeries ="showListSeries"
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
          showListFilms: null,
          showListSeries: null,
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
  },
  showingListFilms(value){
    this.showListFilms = value;
  },
  showingListSeries(value){
    this.showListSeries = value;
  }
},
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import '~mdb-ui-kit/css/mdb.min.css';
#id{
  background-color: black;
}
</style>