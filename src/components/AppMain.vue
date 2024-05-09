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
    <div class="row justify-content-between" v-show="this.store.movieArray.length !== 0">
        <h2>Film</h2>
        <div class="card-container col-2" v-for="curFilm in store.movieArray">
            <MovieCard :cardObj="curFilm" />
        </div>
        
        <h2>Series</h2>
        <div class="card-container col-2" v-for="curSeries in store.tvArray">
            <SeriesCard :cardObj="curSeries" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
</style>