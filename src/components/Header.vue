<template>
<header class="d-flex justify-content-around align-items-center rounded">
    <img src="../assets/logo-boolflix.png" alt="">
    <div>
        <input class="border-0" type="text" v-model="inputText" @keyup.enter= "research()">
        <button class="mx-3 border-0 bg-danger rounded" @click="research()">
        Cerca
    </button>
    </div>
</header>
</template>


<script>
import axios from 'axios';
export default {
name: 'Header',
data(){
    return {
        apiQuery: 'https://api.themoviedb.org/3/search/',
        inputText: '',
        films: null,
        series: null, 
        api:'c485ac33ea061739b9eb0edada7a8d4b',
        language: '',
        show: null,
    };
},
methods: {
    researchMovie(){
        let movieEndpoint  = 'movie';
        let parameters = {
            api_key: this.api,
            language: this.language,
            query: this.inputText,
        };        
        axios.get(`${this.apiQuery}${movieEndpoint}`, 
        {params: parameters}).then((result) => {
            this.films = result.data.results
                this.language = result.data.results.original_language
            if (this.films.length > 0) {
                this.$emit('searchFilms', this.films)
                this.$emit('showFilm', true)
            } else {
                this.$emit('showFilm', false)
            }
            // console.log(this.films)
            // console.log(this.language);
            }).catch((err) => {
                this.$emit('showFilm', false)
                console.log(err);
            });
    },
    researchSeries(){
        let seriesEndpoint  = 'tv';
        let parameters = {
            api_key: this.api,
            language: this.language,
            query: this.inputText,
        };        
        axios.get(`${this.apiQuery}${seriesEndpoint}`, 
        {params: parameters}).then((result) => {
            this.series = result.data.results,
            this.language = result.data.results.original_language,
            this.$emit('searchSeries', this.series)
            if (this.series.length > 0) {
                this.$emit('searchFilms', this.films)
                this.$emit('showSeries', true)
            } else {
                this.$emit('showSeries', false)
            }
            // console.log(this.films)
            // console.log(this.language);
            }).catch((err) => {
                console.log(err);
                this.$emit('showSeries', false)
            });
    },
    research(){
        this.researchMovie();
        this.researchSeries();     
    },
}
}
</script>

<style lang="scss">
    header{
        img{
            height: 70%;
        }
        height: 80px;
        background-color: black;
        input{
            height: 40px;
            background-color: red;
            color: white;
        }
        button{
            height: 40px;
            width: 60px;
        }
    }

</style>