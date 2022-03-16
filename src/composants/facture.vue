<template>

<div class="container">
<br><br>
   <div class="facture text-center">
       <p>code du colis: {{code}}</p>
        <p>description : {{description}}</p>
        <p>depart : {{depart}}</p>
        <p>destination: {{destination}}</p>
        <p>prix: {{prix}} FCFA</p>
        <p> nom expéditeur : {{expediteur}}</p>
        <p>nom destinataire : {{destinataire}}</p>
        <vue-qrcode :value="code"/><br> <br>
        <p><input type="button" value="imprimer" @click="valider" class="btn btn-primary">  <input type="button" value="modifier" @click="annuler" class="btn btn-warning"></p>
   </div>


    <!--<input type="button"  class="btn btn-primary" @click="enregistrer" value="enregistrer"> -->

  </div>

</template>

<script>
import VueQrcode from 'vue-qrcode';


export default{
    
    components: {VueQrcode},

    data() {
    return {
        message: '',
        code1:''
       
    }
    },
    props: {
       
        code: String,
        description: String,
        nombre: String,
        poids: String,
        valeur: String,
        depart: String,
        destination: String,
        prix: String,
        expediteur: String,
        telexp: String,
        cniexp: String,
        destinataire: String,
        teldest: String

    },
    methods : {
        annuler(){
         this.$emit("status")
    },
    

    valider(){
        console.log("clique sur imprimer");
            this.$emit("confirmer");
            

        },

    },
    mounted(){
        
    }
    
   

}
 
</script>

<style>
.facture{
    background-color: cornsilk;
    width: 500px;
    height: 500px;
    

    
}
p{
    font-size: 20px;
    font-family: monospace;
    
}

</style>