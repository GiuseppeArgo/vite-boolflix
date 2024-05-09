<script>
import axios from "axios";

import { store } from './store';

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
    data() {
      return {
        store,
      }
    },
  
    components: {
      AppHeader,
      AppMain,
    },

    methods: {
      SearchSomething() {
          console.log(this.store.searchQuery);
          const paramsobj = {
              api_key: this.store.apiKey,
              query: this.store.searchQuery,
          }
          axios.get("https://api.themoviedb.org/3/search/tv",{
              params: paramsobj
          }).then((resp) => {
              this.store.tvArray = resp.data.results;
              console.log("series",this.store.tvArray);
          });
          axios.get("https://api.themoviedb.org/3/search/movie",{
              params: paramsobj
          }).then((resp) => {
              this.store.movieArray = resp.data.results;
              console.log("film",this.store.movieArray);
          });
    }
  }
}

</script>

<template>
  <AppHeader @searchIn="SearchSomething"/>
  <AppMain />
</template>

<style lang="scss">

</style>
