<template>
<main>
    <ul v-if="filmList.length > 0">
        <h2>MOVIES</h2>
        <CardMovies 
            :filmList ="filmList"  
        />
    </ul>
    <ul v-if="seriesList.length > 0">
        <h2>SERIES</h2>
        <CardSeries 
            :seriesList ="seriesList"
        />
    </ul>
    <div v-else>
        <h2>Nessun risultato trovato</h2>
    </div>
</main>

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