<template>
  <div class='container-fluid'>
    <div class='row mt-5 justify-content-center'>
      <div class='col-2 '>
        <div class="card">
          <div class="card-body">
            <p> HOY </p>
            <p><strong> {{stats.current_time.day}} </strong></p>
            <p> {{stats.current_time.mouth}} {{stats.current_time.year}} </p>
          </div>
        </div>
      </div>
      <div class='col-6 px-1 pt-4 d-flex vhr'>
        <div class='col-4'>
          <div class="card card-in-use">
            <div class="card-body text-center">
              <p> En ruta </p>
              <p> {{stats.bike_stats.use}} </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-free">
            <div class="card-body text-center">
              <p> Inactivas </p>
              <p> {{stats.bike_stats.free}} </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-total">
            <div class="card-body text-center">
              <p> Total </p>
              <p> {{stats.bike_stats.total}} </p>
            </div>
          </div>
        </div>
      </div>
      <div class='col-3'>
        <Chart :height="300" 
          v-if="loaded"
          :chartvalues="[stats.bike_stats.use,stats.bike_stats.free]"
          :options="options"></Chart>
      </div>
    </div>
    <hr/>
    <div class='row mt-5 justify-content-center'>
      <div class='col-10'>
        <h2>Última hora</h2>
        
        <OccupationChart
          :width="1000"
          :chartvaluesUse="generalOccupationData.setEmpty" 
          :chartLabels="generalOccupationData.labels"
          :optionsValues="optionsValues"
          :nameLabel="nameChart[0]"
          :colorChart="colorChart[0]"></OccupationChart>
         <OccupationChart
          :width="1000"
          :chartvaluesUse="generalOccupationData.setFree" 
          :chartLabels="generalOccupationData.labels"
          :optionsValues="optionsValues"
          :nameLabel="nameChart[1]"
          :colorChart="colorChart[1]"></OccupationChart>
      </div>
    </div>
  </div>
</template>

<style scoped>
  p{
    font-size: 2rem;
  }
  .card-total{
    background-color:#ff5900;
    color: white;
  }
  .card-in-use{
    border-color: #ff5900;
  }
  .card-free{
    border-color: #004990;

  }

  .vhr{
    border-right: 1px solid #333;
    border-left: 1px solid #333;

    height:250px;
  }
</style>

<script>
  import axios from "axios";
  import Chart from '@/components/Chart.vue'
  import OccupationChart from '@/components/OccupationChart.vue'

  export default {
    name: 'summarydata',
    components: {
      Chart,
      OccupationChart
    },
    data() {
      return {
        nameChart: ['En uso', 'Inactivas'],
        colorChart: ['#ff5900', '#004990'],
        options: {},
        optionsValues: {
          scales: {
            yAxes: [{
              ticks: {
                beginAtZero: true
              },
              gridLines: {
                display: true
              }
            }],
            xAxes: [ {
              gridLines: {
                display: false
              }
            }]
          },
          legend: {
            display: false
          },
          responsive: true,
          maintainAspectRatio: false
        },
        stats: { current_time:{}, bike_stats: {}},
        loaded: false,
        generalOccupationData: { labels: [], setEmpty: [], setFree: []},
        chartData: null
      };
    },

    methods:{
      async generalStats(){
        let statsApi = await axios.get('http://localhost:5000/api/v1/daily_indicators.json')
        this.stats = await statsApi.data
        this.chartData = await [statsApi.data.bike_stats.use, statsApi.data.bike_stats.free]
        this.loaded = true
        console.log(statsApi.data)
      },
      async occupationData(){
        let occupationApi = await axios.get('http://localhost:5000/api/v1/last_hour.json')
        this.generalOccupationData = await occupationApi.data
        console.log(occupationApi.data.labels)
      }
    },
    async mounted(){
      this.loaded = false
      this.generalStats()
      this.occupationData()
    }
  }
</script>