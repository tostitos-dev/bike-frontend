<script>
  import { Pie, mixins } from "vue-chartjs";
  export default {
    extends: Pie,
    props:{
      chartvalues: Array,
      options: {}
    },
    mounted() {
      // this.chartData is created in the mixin.
      // If you want to pass options please create a local options object
      this.renderChart({
        labels: ["En ruta", "Inactivas"],
        datasets: [
          {
            label: "Summary",
            backgroundColor: ["#ff5900", "#004990"],
            data: this.chartvalues
          }
        ]
      }, this.options);
    }
  };
</script>
