<template>
    <div class="container-fluid h-100" >
            <div class="row h-100">

                <bordlateral data="Gérer Branche" creer="Créer Branche" admin="Gerant Agence" r1="/gerant/creerbranche" r2="/gerant/gererbranche" historique="/agence/historique"></bordlateral>
              <main class="col">
                
                <navbar></navbar>
                <div class="bord"><h3>Tableau de Bord</h3></div>

                <div class="row row-cols-1 row-cols-md-3 g-4">
                   <colislivre></colislivre>

                    <colisarrive></colisarrive>
                    
                    <gain status="branche"></gain>


                    <evolutiongain></evolutiongain>


                     <test></test>

                   
                      <alert></alert>


                  </div>
                
              </main>
          </div>



          


      </div>
</template>

<script>
import bordlateral from './bordlateral.vue'
import navbar from './navbar.vue'
import colislivre from './colislivre.vue'
import colisarrive from './colisarrive.vue'
import gain from './gain.vue'
import evolutiongain from './evolutiongain.vue'
import test from './test.vue'
import alert from './alert.vue'


export default {
  components: {bordlateral, navbar, colislivre, colisarrive, gain, evolutiongain, test, alert},
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    } 
  }
}
</script>