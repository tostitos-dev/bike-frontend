<script>
  import { Pie, mixins } from "vue-chartjs";
  export default {
    extends: Pie,
    props: {
      chartData: {
        type: Array | Object,
        required: false
      }
    },
    mounted() {
      // this.chartData is created in the mixin.
      // If you want to pass options please create a local options object
      this.renderChart({
        chartLabels: ["En ruta", "Inactivas"],
        datasets:[
          {
            label: "Data One",
            backgroundColor: ["#ff5900", "#004990"],
            data: this.chartData
          }
        ]  
      }, this.options);
    }
  };
</script>
