<template>
<div>
  <h1>Welcome to Studio Ghibli</h1>
  <v-select :options="films" label="title" v-model="currentFilm"></v-select>
  <selected-film :currentFilm="currentFilm"></selected-film>
</div> 
</template>

<script>
import SelectedFilm from './components/SelectedFilm.vue'

export default {
  name: "app",
  data(){
    return {
      films: [],
      currentFilm: null
    }
  },

  components: {
    'selected-film': SelectedFilm
  },

  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)
  }
  
}
</script>

<style scoped>

</style>
