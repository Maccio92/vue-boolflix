<template>
<main class="text-white">
    <div class="container">
        <div class="row row-cols-12 justify-content-center">
                <div class="text-center" v-show="welcome">
                    <h2>Benvenuto!</h2>
                    <button @click="start(welcome)" class="m-2 border-0 bg-danger rounded">Clicca per iniziare</button>
                </div>
                <div class="container" v-if="showingFilm">
                    <h2 class="mb-1">MOVIES</h2>
                        <CardMovies 
                            :filmList ="filmList" 
                        />
                </div>
                <div class="row" v-else-if="showingFilm == false">
                    <h2>Nessun risultato trovato</h2>
                </div>
        </div>
        <div class="row row-cols-12 justify-content-between mt-3">
            <div class="container" v-if="showingSeries">
                    <h2 class="mb-1">SERIES</h2>
                        <CardSeries 
                            :seriesList ="seriesList"
                        />
            </div>
            <div class="row" v-else-if="showingSeries == false">
                <h2>Nessun risultato trovato</h2>
            </div>
        </div>
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
    data(){
        return{
            welcome: true,
        }
    },
    props: ["filmList", "seriesList", "showingFilm", "showingSeries"],
    methods: {
        start(){
            this.welcome = false;
        }    
    },
}

</script>

<style>
main{
    height: calc(100vh - 80px);
}
</style>