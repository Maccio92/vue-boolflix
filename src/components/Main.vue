<template>
<div>
<CardMovies 
    v-for="(film, index) in filmList" 
    :key="index"
    :filmList ="filmList"  
/>
<CardSeries 
    v-for="(series, index) in seriesList" 
        :key="index"
        :seriesList ="seriesList"
/>
</div>

</template>

<script>
import CardMovies from './CardMovies.vue';
import CardSeries from './CardSeries.vue';

export default {
    name: 'Main',
    components: {
        CardMovies,
        CardSeries,
    },
    props: ["filmList", "seriesList"],
    
}
</script>

<style>

</style>