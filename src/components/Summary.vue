<template>
  <div class='container-fluid'>
    <div class='row mt-5 justify-content-center'>
      <div class='col-2 '>
        <div class="card">
          <div class="card-body">
            <p> HOY </p>
            <p><strong> {{stats.current_time.day}} </strong></p>
            <p> JUN 2019 </p>
          </div>
        </div>
      </div>
      <div class='col-6 px-1 pt-4 d-flex vhr'>
        <div class='col-4'>
          <div class="card card-in-use">
            <div class="card-body text-center">
              <p> En ruta </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-free">
            <div class="card-body text-center">
              <p> Inactivas </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-total">
            <div class="card-body text-center">
              <p> Total </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
      </div>
      <div class='col-3'>
        <Chart :height="300" :data="chartData"></Chart>
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

  export default {
    name: 'summarydata',
    components: {
      Chart
    },
    data() {
      return {
        chartData: {
          labels: ["En ruta", "Inactivas"],
          datasets: [
            {
              label: "Data One",
              backgroundColor: ["#ff5900", "#004990"],
              data: [10, 10]
            }
          ]
        },
        stats: {JSON}
      };
    },

    methods:{
      async generalStats(){
        let statsApi = await axios.get('http://localhost:3000/api/v1/daily_indicators.json')
        this.stats = await statsApi.data
        console.log(statsApi.data)
      }
    },
    created(){
      this.generalStats()
    }
  }
</script>