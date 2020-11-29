<template>
    <section v-if="currentFilm" class="film-detail">
        <h2>{{ currentFilm.title }}</h2>
        <p><b>Relese Date:</b> {{ currentFilm.release_date }}</p>
        <p><b>Director:</b> {{ currentFilm.director }}</p>
        <p><b>Producer:</b> {{ currentFilm.producer }}</p>
        <p><b>Plot:</b> {{ currentFilm.description }}</p>
        <species-chart :species="getSpeciesURL" ></species-chart>
    </section>
</template>

<script>
import SpeciesChart from './SpeciesChart.vue'

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
        'species-chart': SpeciesChart
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