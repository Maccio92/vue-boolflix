<template>
<div>
    <ul>
        <li v-for="(series, index) in seriesList" 
            :key="index">
            <h2>{{series.name}}</h2>
            <h3>{{series.original_name}}</h3>
            
            <h4>
                <i :class="'flag flag-' +  getFlag(series.original_language)"></i>
            </h4>
            
            <h5>{{series.vote_average}}</h5>
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
        }
    }
}
</script>

<style>

</style>