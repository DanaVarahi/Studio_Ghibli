<template>
  <div>
    <div id="chart_div2"></div>
</div>
</template>

<script>
export default {
    name: 'vehicles-chart',
    data(){
        return{
            vehiclesData: []
        }
    },

    props: ['vehicles'],

    watch: {
        vehicles: function(){
            this.processUrls()
        }
    },

    mounted:function(){
            this.processUrls()
        },   

    methods: {
        processVehiclesData: function(data){
            
            const vehiclesDone = []

            for ( const vehicle of data){

                const vehicleClass = vehicle.vehicle_class
                const totalVehicles = 1
                const vehiclesTotal = [vehicleClass, totalVehicles]
                 if (vehiclesDone.includes(vehicleClass)){
                 
                    for (const array in this.vehiclesData){
                        if(array[0] == vehicleClass){
                            array[1]++ 
                        }
                    }

                 } else {
                        vehiclesDone.push(vehicleClass)
                        this.vehiclesData.push(vehiclesTotal)
                 }

                
            }
            this.drawChart()
        },

         drawChart: function() {

            var data = new google.visualization.DataTable();
            data.addColumn('string', 'Vehicles');
            data.addColumn('number', 'Total');
            data.addRows( this.vehiclesData );

            var options = {'title':'Vehicles in the film',
                            'width':400,
                            'height':300,
                            'is3D': true,
                            'colors':['#E0D991','#91DBE0','#D691E0'],
                            'fontName': 'Lora',
                            'titleTextStyle': {'fontSize': 15, 
                                                'color': '927E31'}
                            };

            var chart = new google.visualization.PieChart(document.getElementById('chart_div2'));
            chart.draw(data, options);
        },

        processUrls: function(){
            this.vehiclesData = []
            let res
                fetch(this.vehicles[0])
                .then(res => res.json())
                .then( data => this.processVehiclesData(data))
            

            return this.vehiclesData
        }
    }
}
</script>

<style scoped>

</style>