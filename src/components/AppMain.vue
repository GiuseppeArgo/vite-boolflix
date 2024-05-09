<script>
import { store } from '../store';

import AppCard from "./AppCard.vue";

export default {
    components: {
        AppCard,
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
            <AppCard :cardObj="curFilm" />
        </div>
        
        <h2>Series</h2>
        <div class="card-container col-2" v-for="curSeries in store.tvArray">
            <AppCard :cardObj="curSeries" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
</style>