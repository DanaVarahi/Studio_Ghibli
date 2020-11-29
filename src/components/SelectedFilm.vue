<template>
    <section v-if="currentFilm" class="film-detail">
        <h2>{{ currentFilm.title }}</h2>
        <p><b>Relese Date:</b> {{ currentFilm.release_date }}</p>
        <p><b>Director:</b> {{ currentFilm.director }}</p>
        <p><b>Producer:</b> {{ currentFilm.producer }}</p>
        <p><b>Plot:</b> {{ currentFilm.description }}</p>
        <div id="charts">
            <species-chart :species="getSpeciesURL" ></species-chart>
            <vehicles-chart :vehicles="getVehiclesURL" ></vehicles-chart>
        </div>
    </section>
</template>

<script>
import SpeciesChart from './SpeciesChart.vue'
import VehiclesChart from './VehiclesChart.vue'

export default {
    name: 'selected-film',
    props: ['currentFilm'],
    data(){
        return {
            species:[],
            vehicles: [],
        }
    },

    computed: {
        getSpeciesURL: function(){
            return this.currentFilm.species
        },

        getVehiclesURL: function(){
            return this.currentFilm.vehicles
        }
    },

    components: {
        'species-chart': SpeciesChart,
        'vehicles-chart': VehiclesChart
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

#charts {
    display: flex;
    justify-content: center;
}

@media only screen and (max-width: 930px) {
#charts {
    flex-direction: column;
}
}
</style>