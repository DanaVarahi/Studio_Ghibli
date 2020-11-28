<template>
<div>
  <h1>Welcome to Studio Ghibli</h1>
  <v-select :options="films" label="title" v-model="selectedFilm"></v-select>
  <p>{{ selectedFilm }}</p>
</div> 
</template>

<script>
export default {
  name: "app",
  data(){
    return {
      films: [],
      selectedFilm: null
    }
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
