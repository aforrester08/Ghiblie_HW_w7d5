<template lang="html">
  <div>
    <h1>App.vue here</h1>
    <list-films :filmData="filmData"></list-films>
    <film-detail :film="selectedFilm"></film-detail>
  </div>
</template>

<script>
import ListFilms from './components/ListFilms.vue'
import FilmDetails from './components/FilmDetails.vue'
import {eventBus} from './main.js'

export default {
  name: "app",
  data() {
    return {
      filmData: [],
      selectedFilm: null
    }
  },
  mounted(){
    eventBus.$on('selected-film', (film) =>
    this.selectedFilm = film);

    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(data => this.filmData = data);
  },
  components:{
    "list-films": ListFilms,
    "film-detail": FilmDetails
  }

}
</script>

<style lang="css" scoped>
</style>
