<template>
  <div class="container-fluid h-100">
    <div class="row h-100 ">
     <bordlateral data="Gérer Branche" creer="Créer Branche" admin="Gerant Agence" r1="/gerant/creerbranche" r2="/gerant/gererbranche" historique="/agence/historique"></bordlateral>
      <main class="col">
        <navbar></navbar>
        <div class="bord">
          <h2 class="text-center">Historique des colis</h2>
        </div>

        <div class="row row-cols-1 row-cols-md-3 g-4">
          <br />
         
        <p class="text-center">Total:{{total}} </p>
       <div class="filtre">
          <p>filtre</p>
        <p> date debut:<input type="date" v-model="datedebut"></p>
        <p> date de fin: <input type="date" v-model="datefin"></p>
        <p><input type="button" value="filtrer" @click="filtrer"></p>
       </div>
          <table class="table table-success table-striped">
  <thead>
    <tr>
        <th scope="col">N° </th>
      <th scope="col">Nom Branche</th>
      <th scope="col">Nombre de colis </th>
      <th scope="col">Montant </th>
      
    </tr>
  </thead>
  <tbody>
    <tr scope="row" v-for="(element,index) in tableau" :key="index"> 
      <!-- scope="row" v-for="element in tableau" :key="element.code">{{element.code}} -->
       <th > {{index}}</th>
      <td> {{element.nom}}</td>
      <td> {{element.nombre}}</td>
      <th>{{element.som}}</th>
     

    </tr>
   
  </tbody>
</table>
         
            

        </div>
      </main>
    </div>
  </div>
</template>

<script>
import bordlateral from "./bordlateral.vue";
import navbar from "./navbar.vue";



export default {
  name: "app",
  components: { bordlateral, navbar },
  data() {
    return {
      tableau:[],
      total:10,
      datedebut: new Date(),
      datefin: new Date()
    
    };
  },
  methods: {
    filtrer(){
      let tempo= 0;
      let tempdate = new Date();
        let context = this;
        context.datefin = tempdate.setDate(new Date(context.datefin).getDate()+1);
        console.log("---"+context.datefin);


      const filtre = {datedebut: context.datedebut, datefin: context.datefin}
 console.log((context.datedebut));
 //611bca36609fe50e2eedbae8
  axios.post("http://localhost:5000/api/infos/agence/historiquefiltre/6112eed4ff8af9169c99587f", filtre)
  .then(response => {
    context.tableau = response.data ;
    console.log(context.tableau);

    for(let i=0; i<context.tableau.length; i++){
       tempo+= context.tableau[i].som;

      }
      context.total= tempo ;
      
  } )

    }
  },
  mounted(){
 
  let context = this ;
  let tempo=0;
 
  //611bc8be609fe50e2eedbae3
    axios.get("http://localhost:5000/api/infos/agence/historique/6112eed4ff8af9169c99587f")
    .then(response => {console.log(response.data)
      
     context.tableau = response.data;

   for(let i=0; i<context.tableau.length; i++){
       tempo+= context.tableau[i].som;

      }
      context.total= tempo ;
    
    })

  }
  
  
};
</script>