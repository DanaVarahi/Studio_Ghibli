<template>
<div>
    <p>{{ speciesData }}</p>  
</div>

</template>

<script>
export default {
    name: 'species-list',
    data(){
        return {
            speciesData: []
        }
    },
    props: ['species'],
    
    watch: {
        immediate: true,
        species: function(){
            this.speciesData = []
            console.log(this.species)
            let res
            for ( const url of this.species){
                console.log(url)
                fetch(url)
                .then(res => res.json())
                .then( data => this.processSpeciesData(data))
            }

            return this.speciesData
        }  
    },

    methods: {
        processSpeciesData: function(data){
            const speciesName = data.name
            const totalCharacters = data.people.length

            const speciesTotal ={
                name: speciesName,
                total: totalCharacters
            }
            this.speciesData.push(speciesTotal)
        }
    }
}

</script>

<style>

</style>