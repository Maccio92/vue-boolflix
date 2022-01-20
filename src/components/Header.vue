<template>
<div>
    <input type="text" v-model="inputText">
    <button @click=" researchSeries();">
        Cerca
    </button>
</div>
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
        api:'c485ac33ea061739b9eb0edada7a8d4b',
        language: '',
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
            this.films = result.data.results,
            this.language = result.data.results.original_language,
            this.$emit('search', this.films)
            console.log(this.films)
            console.log(this.language);
            }).catch((err) => {
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
            this.films = result.data.results,
            this.language = result.data.results.original_language,
            this.$emit('search', this.films)
            console.log(this.films)
            console.log(this.language);
            }).catch((err) => {
                console.log(err);
            });
    }
}
}
</script>

<style>

</style>