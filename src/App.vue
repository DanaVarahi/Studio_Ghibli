<template>
<div>
  <h1>Welcome to Studio Ghibli</h1>
  <p>{{ films }}</p>
</div> 
</template>

<script>
export default {
  name: "app",
  data(){
    return {
      films: [] 
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
