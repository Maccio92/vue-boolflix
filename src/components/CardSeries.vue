<template>
<div>
    <ul>
        <li>
            <h2>{{series.name}}</h2>
            <h3>{{series.original_name}}</h3>
            
            <h4>
                <i :class="(series.original_language == 'en') ? 'flag flag-us' : 'flag flag-' + series.original_language "></i>
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
}
</script>

<style>

</style>