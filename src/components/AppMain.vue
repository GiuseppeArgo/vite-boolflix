<script>
import { store } from '../store';

import MovieCard from "./MovieCard.vue";
import SeriesCard from "./SeriesCard.vue"

export default {
    components: {
        MovieCard,
        SeriesCard,
    },

    data(){
        return{
            store,
        }
    },
}
</script>

<template>
<main>
    <div class="list container-fluid">
        <h2 class="p-5">Film</h2>
        <ul class="d-flex flex-wrap justify-content-around">
            <li v-for="curFilm in store.movieArray" class="list-item">
                <MovieCard :cardObj="curFilm" />
            </li>
        </ul>
        
        <h2 class="p-5">Series</h2>
        <ul class="d-flex flex-wrap justify-content-around">
            <li v-for="curSeries in store.tvArray" class="list-item">
                <SeriesCard :cardObj="curSeries" />
            </li>
        </ul>
    </div>
</main>
</template>

<style lang="scss" scoped>

main {
    background-color: grey;
    height: calc(100vh - 80px);
    overflow: auto;
    color: white;
}

.list {
    margin: 0 auto;
}

.list-item{
    width: 300px;
    list-style-type: none;
    margin: 20px;
}

</style>