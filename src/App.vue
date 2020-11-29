<template>
<div>
  <header></header>
  <div id="content">
    <h1>Select a film:</h1>
    <v-select :options="films" label="title" v-model="currentFilm"></v-select>
    <selected-film :currentFilm="currentFilm"></selected-film>
  </div>
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
#content{
  width: 70%;
  margin: auto;
}

h1 {
  font-family: 'Lora', serif;
  color: rgb(143, 126, 49);
}

.v-select {
  font-family: 'Lora', serif;
}

header {
  background-image: url('./assets/ghibli_logo_gold.png');
  background-repeat:  no-repeat;
  background-position: center;
  height: 15em;
}

@media only screen and (max-width: 700px){
  #content{
  width: 100%;

}
}

</style>
