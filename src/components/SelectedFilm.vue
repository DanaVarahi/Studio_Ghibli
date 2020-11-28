<template>
    <section v-if="currentFilm" class="film-detail">
        <h2>{{ currentFilm.title }}</h2>
        <p>Relese Date: {{ currentFilm.release_date }}</p>
        <p>Director: {{ currentFilm.director }}</p>
        <p>Producer: {{ currentFilm.producer }}</p>
        <p>Plot: {{ currentFilm.description }}</p>
        <species-list :species="getSpeciesURL" ></species-list>
    </section>
</template>

<script>
import SpeciesList from './SpeciesList.vue'

export default {
    name: 'selected-film',
    props: ['currentFilm'],
    data(){
        return {
            species:[],
        }
    },

    computed: {
        getSpeciesURL: function(){
           
            return this.currentFilm.species
             console.log(species)
        }
    },

    components: {
        'species-list': SpeciesList
    }
}
</script>

<style scoped>
h2 {
    font-family: 'Lora', serif;
    color: darkblue;
}

.film-detail{
     font-family: 'Lora', serif;
}
</style>