<template>
<div class="container">
    <ul class="list-unstyled ">
        <li class="my-3 p-3 rounded-7 shadow" v-for="(series, index) in seriesList" 
            :key="index">
            <div class="d-flex justify-content-start align-items-center" >
                <img :src="'http://image.tmdb.org/t/p/w342' + series.poster_path" alt="">
                <div class="ps-5">
                    <p class="mb-1">Titolo</p>
                    <h2 class="fs-4 text mb-3">{{series.name}}</h2>
                    <p class="mb-1" >Titolo originale</p>
                    <h3 class="fs-5 text mb-3">{{series.original_name}}</h3>
                    <p class="mb-1">Lingua originale</p>
                    <i :class="'mb-3 flag flag-' +  getFlag(series.original_language)"></i>
                    <div>
                        <p class="mb-1">Voto</p>
                        <div>
                            <i v-for="(star, index) in 5" 
                            :key="index" 
                            :class="(index < getValutation(series.vote_average) ? 'fas fa-star' : 'far fa-star')"></i>
                        </div>  
                    </div>
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
    height: 400px;
    background-color: rgba($color: #181818, $alpha: 0.7);
    div{
        height: 100%;
    
    img{
    height: 100%;
    }
    }
    p{
        color: gray;
    }
}
</style>