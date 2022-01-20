<template>
<div>
    <ul>
        <li v-for="(film, index) in filmList" :key="index">
            <h2>{{film.name}}</h2>
            <h3>{{film.original_name}}</h3>
            
            <h4>
                <i :class="(film.original_language == 'en') ? 'flag flag-us' : 'flag flag-' + film.original_language "></i>
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

}
</script>

<style>

</style>