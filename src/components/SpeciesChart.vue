<template>
<div>
    <div id="chart_div"></div>
</div>

</template>

<script>


export default {
    name: 'species-chart',
    data(){
        return {
            speciesData: []
        }
    },
    props: ['species'],

    watch: {
        // immediate: true,
        species: function(){
           this.processUrls()
        }  
    },

    mounted:function(){
            this.processUrls()
        },    
    

    methods: {
       
        processSpeciesData: function(data){
            const speciesName = data.name
            const totalCharacters = data.people.length

            const speciesTotal =[ speciesName,  totalCharacters]
            this.speciesData.push(speciesTotal)
            this.drawChart()
        },

        drawChart: function() {

        // Create the data table.
            var data = new google.visualization.DataTable();
            data.addColumn('string', 'Species');
            data.addColumn('number', 'Total');
            data.addRows( this.speciesData );

        // Set chart options
            var options = {'title':'Species of the Characters',
                            'width':400,
                            'height':300};

        // Instantiate and draw our chart, passing in some options.
            var chart = new google.visualization.PieChart(document.getElementById('chart_div'));
            chart.draw(data, options);
        },

        processUrls: function(){
            this.speciesData = []
            let res
            for ( const url of this.species) {
               
                fetch(url)
                .then(res => res.json())
                .then( data => this.processSpeciesData(data))
            }

            return this.speciesData
        }

    }
}

</script>

<style>

</style>