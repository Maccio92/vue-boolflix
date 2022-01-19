<template>
<div>
    <input type="text" v-model="inputText">
    <button @click="research">
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
    inputText: '',
    films: null, 
    };
},
methods: {
    research(){
        axios.get("https://api.themoviedb.org/3/search/movie?api_key=c485ac33ea061739b9eb0edada7a8d4b",
        {
        params: {
            query: this.inputText
        }
    }).then((result) => {
        this.films = result.data.results,
        this.$emit('search', this.films)
        console.log(this.films)
    }).catch((err) => {
        console.log(err);
    });
}
}
}
</script>

<style>

</style>