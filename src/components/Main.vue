<template>
<div>
    <ul>
        <li v-for="(film, index) in filmList" :key="index">
            <h2>{{film.title}}</h2>
            <h3>{{film.original_title}}</h3>
            <h4>{{film.original_language}}</h4>
            <h5>{{film.vote_average}}</h5>
        </li>
    </ul>
    
</div>
</template>

<script>
export default {
    name: 'Main',
    props: ["filmList"],

}
</script>

<style>

</style>