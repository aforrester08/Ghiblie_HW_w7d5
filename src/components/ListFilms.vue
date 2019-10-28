<template lang="html">
<div class="">
  <ul v-model="selectedFilm"  @click="handleClick">
      <li v-for="film in filmData" :value="film">{{film.title}}</li>
  </ul>
</div>


</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-films',
  props: ['filmData'],
  data() {
    return {
      selectedFilm: null
    }
  },
  methods: {
    handleClick() {
      console.log(selectedFilm);
      eventBus.$emit('film-selected', this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
