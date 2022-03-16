<template>
    <div class="col-8">
  <div class="card  h-100">
    <p class="text-center text-primary card-header">EVOLUTION DES GAINS</p>
    <div class="card-body">
      <h5 class="card-title"></h5>
      <p class="card-text text-center">502150 <!-- <line-chart :chartData="nom" :options="chartOptions" label="positive">  </line-chart> --></p><br><br><br>
     
      <chart></chart>
    </div>
  </div>
</div>

</template>

<script>
import chart from './RandomChart.vue'

export default {
  components: {
   chart
  },
    data () {
    return {
      nom: [],
      nombre: [],
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false
      }
      
    } 
  },

  async created(){
    const {data} = await axios.get("http://localhost:5000/api/user");
     let i= 0;
     data.forEach(d => {
       const nom = d.nom;
       i++;
       this.nom.push({nom:nom, num: i})
     
     });

  }
 
}
</script>