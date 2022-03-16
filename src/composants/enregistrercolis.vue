<template>
  <div class="container-fluid h-100">
    <div class="row h-100 ">
      <bordlateral  creer="Enregistrer un colis" data="envoi" admin="Gérant de branche" branche1="reception" r1="/branche/enregistrer" r2="/branche/envoi" historique="/branche/historique"></bordlateral>
      <main class="col">
        <navbar></navbar>
        <div class="bord">
         <br>
        </div>

        <div class="row row-cols-1 row-cols-md-3 g-4">
          <br />
          <form v-if="!status"  class="enregistrement ">
             <h2>Enregistrer un colis</h2>
            <br>
            <div class=" row row-cols-1 row-cols-md-3 g-4">

            <div class="mb-3 ">
              
              description:<input
                type="text"
                class="form-control" v-model="description"
                placeholder="description" 
              />
             
            </div>
            <div class="mb-3">
              
              nombre<input
                type="number"
                class="form-control" v-model="nombre"
                placeholder="nombre"
              />
                
            </div>
            <div class="mb-3">
              
              poids<input
                type="number"
                class="form-control" v-model="poids"
                placeholder="poids"
              />
            </div>
            <div class="mb-3">
              
              valeur<input
                type="number"
                class="form-control" v-model="valeur"
                placeholder="valeur"
              />
            </div>
            <div class="mb-3">
              
              depart<input
                type="text"
                class="form-control" v-model="depart"
                placeholder="depart"
              />
            </div>
            <div class="mb-3">
              
              destination<input
                type="text"
                class="form-control" v-model="destination"
                placeholder="destination"
              />
            </div>

            <div class="mb-3">
              
              prix<input
                type="number"
                class="form-control" v-model="prix"
                placeholder="prix"
              />
            </div>

            <div class="mb-3">
              
              nom expéditeur<input
                type="text"
                class="form-control" v-model="nomExp"
                placeholder="nom expéditeur"
              />
            </div>
            <div class="mb-3">
              
              tel expéditeur<input
                type="text"
                class="form-control" v-model="telExp"
                placeholder="tel expéditeur"
              />
            </div>
            <div class="mb-3">
              
              cni expéditeur<input
                type="text"
                class="form-control" v-model="cniExp"
                placeholder="cni expéditeur"
              />
            </div>
            <div class="mb-3">
              
              nom destinataire<input
                type="text"
                class="form-control" v-model="nomDest"
                placeholder="nom destinataire"
              />
            </div>
            <div class="mb-3">
              
              tel destinataire<input
                type="text"
                class="form-control" v-model="telDest"
                placeholder="tel destinataire"
              />
            </div>
           
            
            </div>
             

           
            <input type="button"  class="btn btn-primary btn-enregistrer" @click="enregistrer" value="enregistrer">
            

          </form>

          
            <div class="col">
         
              <facture v-if="status" @status="changestatus" @confirmer="confirmation"  :code="code" :description="description" :nombre="nombre" :poids="poids" :valeur="valeur" :depart="depart" :destination="destination" :prix="prix" :expediteur="nomExp" :telexp="telExp" :cniexp="cniExp" :destinataire="nomDest" :teldest="telDest"> </facture>
             </div>
         
            

        </div>
      </main>
    </div>
  </div>
</template>

<script>
import bordlateral from "./bordlateral.vue";
import navbar from "./navbar.vue";
import facture from './facture.vue'


export default {
  name: "app",
  components: { bordlateral, navbar,facture },
  data() {
    return {
      c: "Welcome to Your bord lateral",
      code:'',
      description:'',
      nombre:'',
      poids:'',
      valeur:'',
      depart:'',
      destination:'',
      prix:'',
      nomExp:'',
      telExp:'',
      cniExp:'',
      nomDest:'',
      telDest:'',
      id:'',
      status:false,
         

    };
  },
  methods: {

      enregistrer(){
        
         let context = this;
        const article = {depart: this.depart , destination: this.destination};
        axios.post("http://localhost:5000/api/colis/count", article)
        .then(response  =>{ console.log(response);
            context.code = response.data ;
        })
         console.log("enregistrer");
      this.status = true;
      },

    confirmation(){
      
    let context = this ;
    
      const article = { description: this.description, nombre:this.nombre , poids: this.poids, valeur:this.valeur , depart: this.depart, destination:this.destination, prix: this.prix, nomExp: this.nomExp, telExp: this.telExp, cniExp: this.cniExp, nomDest: this.nomDest, telDest: this.telDest};
  //611bca36609fe50e2eedbae8
  axios.post("http://localhost:5000/api/colis/register/611bc8be609fe50e2eedbae3", article)
    .then(response => {console.log(response.data);
    context.code= response.data.code
    console.log("le status "+context.code);
    })
   
  
   
    },

    changestatus(){
        this.status = false ;
    }
  },

  
  
  
};
</script>

<style>
.enregistrement{
  background-color: rgb(255, 255, 255);
  
  float: right; 
 

   margin: auto;
  width: 80%;
  height: 600px;
  border: 3px solid rgb(212, 219, 212);
  padding: 10px;

}
.btn-enregister{
   margin: auto;
  width: 50%;
  text-align: center;
  
 
  padding: 10px;
}
</style>