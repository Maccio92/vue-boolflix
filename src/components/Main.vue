<template>
<main>
    <ul v-if="showingFilm">
        <h2>MOVIES</h2>
        <CardMovies 
            :filmList ="filmList"  
        />
    </ul>
    <div v-else-if="showingFilm == false">
        <h2>Nessun risultato trovato</h2>
    </div>
    <ul v-if="showingSeries">
        <h2>SERIES</h2>
        <CardSeries 
            :seriesList ="seriesList"
        />
    </ul>
    <div v-else-if="showingSeries == false">
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
    props: ["filmList", "seriesList", "showingFilm", "showingSeries"],
    
}
</script>

<style>

</style>