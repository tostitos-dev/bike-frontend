<script>
  import { Line, mixins } from "vue-chartjs";
  export default {
    extends: Line,
    props:{
      nameLabel: String,
      colorChart: String,
      optionsValues: {},
      chartvaluesUse: {
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
            label: this.nameLabel,
            data: this.chartvaluesUse,
            borderColor: this.colorChart,
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
          }
        ]
      }, this.options);
    },
    watch: { 'chartvaluesUse': function(){ this.renderChart({
        labels: this.chartLabels,
        datasets: [
          {
            label: this.nameLabel,
            data: this.chartvaluesUse,
            borderColor: this.colorChart,
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
          }
        ]
      }, this.options); } },
  };
</script>
