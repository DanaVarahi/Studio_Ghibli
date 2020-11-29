<template>
    <section v-if="currentFilm" class="film-detail">
        <h2>{{ currentFilm.title }}</h2>
        <p><b>Relese Date:</b> {{ currentFilm.release_date }}</p>
        <p><b>Director:</b> {{ currentFilm.director }}</p>
        <p><b>Producer:</b> {{ currentFilm.producer }}</p>
        <p><b>Plot:</b> {{ currentFilm.description }}</p>
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
    color:  rgb(143, 126, 49);
}

.film-detail{
     font-family: 'Lora', serif;
}

</style>