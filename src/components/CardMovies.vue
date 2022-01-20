<template>
<div>
    <ul>
        <li v-for="(film, index) in filmList" 
            :key="index">
            <h2>{{film.title}}</h2>
            <h3>{{film.original_title}}</h3>
            
            <h4>
                <i :class="'flag flag-' +  getFlag(film.original_language)"></i>
            </h4>
            
            <h5>{{film.vote_average}}</h5>
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

<style>

</style>