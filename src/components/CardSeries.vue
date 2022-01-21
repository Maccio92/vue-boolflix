<template>
<div class="row row-cols-12 ">
    <ul class="list-unstyled list-inline d-flex flex-wrap gap-4 justify-content-around">
        <li class="col-2 list-inline-item justify-content-center" v-for="(series, index) in seriesList" 
            :key="index">
                <img class="img-fluid" :src="'http://image.tmdb.org/t/p/w342' + series.poster_path" alt="">
                <div class="p-3 overlay">
                    <p class="mb-1">Titolo</p>
                    <h2 class=" mb-3">{{series.name}}</h2>
                    <p class="mb-1 " >Titolo originale</p>
                    <h3 class=" mb-3">{{series.original_name}}</h3>
                    <p class="mb-1 ">Lingua originale</p>
                    <i :class="'mb-3 flag flag-' +  getFlag(series.original_language)"></i>
                    <div>
                        <p class="mb-1">Voto</p>
                        <div>
                            <i v-for="(star, index) in 5" 
                            :key="index" 
                            :class="(index < getValutation(series.vote_average) ? 'fas fa-star' : 'far fa-star')"></i>
                        </div> 
                        <p class="mt-2">"{{(series.overview != "") ? series.overview : "Descrizione non disponibile" }}"</p>
                    </div>
                </div>
        </li>
    </ul>   
</div>
</template>

<script>
export default {
    name: 'CardSeries',
    props: ["seriesList"],
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
        },
        getValutation(vote){
        return Math.round (vote / 2);
    }
    },
}
</script>

<style lang="scss">
li{
    height: 350px;
    position: relative;
    &:hover .overlay{
        display: block;
        cursor: pointer;
    }
    .overlay{
    background-color: black;
    display: none;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 80%;
        p{
        font-size: 0.8em;
        color: gray;
        }
        h2{
                font-size: 1em;
        }
    } 
    
}
</style>