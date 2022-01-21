<template>
<div class="container">
    <ul class="list-unstyled ">
        <li class="my-3 p-3 rounded-7 shadow" v-for="(film, index) in filmList" 
            :key="index">
            <div class="d-flex justify-content-start align-items-center" >
                <img :src="'http://image.tmdb.org/t/p/w500' + film.poster_path" alt="">
                <div class="ps-5">
                    <p class="mb-1">Titolo</p>
                    <h2 class="fs-4 text mb-3">{{film.title}}</h2>
                    <p class="mb-1" >Titolo originale</p>
                    <h3 class="fs-5 text mb-3">{{film.original_title}}</h3>
                    <p class="mb-1">Lingua originale</p>
                    <i :class="'mb-3 flag flag-' +  getFlag(film.original_language)"></i>
                    <p class="mb-1">Voto</p>
                    <h5 class="fs-5 text mb-3">{{film.vote_average}}</h5>
                </div>
            </div>
        </li>
    </ul>   
</div>
</template>

<script>
export default {
    name: 'CardMovies',
    props: ["filmList"],
    methods: {
    getFlag(lang) {
            switch (lang){
            case 'en':
                return 'us';
            case 'ko':
                return 'kr';
            case 'ja':
                return 'jp';
            case 'ur':
                return 'pk';
            case 'zh':
                return 'cn';
            default:
                return lang
            }
        }
    }
}
</script>

<style lang="scss">
li{
    height: 400px;
    background-color: rgba($color: #181818, $alpha: 0.7);
    img{
    height: 100%;
    }
    p{
        color: gray;
    }
}

</style>    