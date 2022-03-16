<script>
import {Line,Bar} from 'vue-chartjs';

export default {
  extends:Line,
  mixins: [Bar],
  props: {
    label: {
      type: String
    },
    chartData: {
      type: Array
    },
    options: {
      type: Object
    }


  },
  mounted(){
    console.log("---------------------------");
    const noms = this.chartData.map(d => d.nom).reverse();
    //const nums = this.chartData.map(d => d.num).reverse();

    this.renderChart(this.chartData,
    /*  labels: noms,
      datasets: [{
        label: this.label,
        data: nums}]
    },*/
    this.options
    );
  }
}
</script>