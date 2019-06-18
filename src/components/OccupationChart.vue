<script>
  import { Line, mixins } from "vue-chartjs";
  export default {
    extends: Line,
    props:{
      optionsValues: {},
      chartvaluesUse: {
        type: Array,
        required: true
      },
      chartvaluesFree: {
        type: Array,
        required: true
      },
      chartLabels: {
        type: Array,
        required: true
      }
    },
    data () {
      return {
        options: {
          lineTension: 1,
          scales: {
            yAxes: [{
              ticks: {
                beginAtZero: false,
                
                stepSize: 3
              
              },
              gridLines: {
                display: true
              }
            }],
            xAxes: [ {
              gridLines: {
                display: false
              },
              ticks:{
                autoSkip: true,
                maxTicksLimit: 30
              }
            }]
          },
          legend: {
            display: true
          },
          responsive: true,
          maintainAspectRatio: false
        }
      }
    },
    mounted() {
      this.renderChart({
        labels: this.chartLabels,
        datasets: [
          {
            label: "En ruta",
            data: this.chartvaluesUse,
            borderColor: '#ff5900',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
          },
          // {
          //   label: "Inactivas",
          //   borderColor: '#004990',
          //   pointBackgroundColor: 'white',
          //   borderWidth: 1,
          //   pointBorderColor: '#249EBF',
          //   backgroundColor: 'transparent',
          //   data: this.chartvaluesFree
          // }
        ]
      }, this.options);
    },
    watch: { 'chartvaluesUse': function(){ this.renderChart({
        labels: this.chartLabels,
        datasets: [
          {
            label: "En ruta",
            data: this.chartvaluesUse, 
            borderColor: '#ff5900',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
          },
          // {
          //   label: "Inactivas",
          //   borderColor: '#004990',
          //   pointBackgroundColor: 'white',
          //   borderWidth: 1,
          //   pointBorderColor: '#249EBF',
          //   backgroundColor: 'transparent',
          //   data: this.chartvaluesFree
          // }
        ]
      }, this.options); } },
  };
</script>
