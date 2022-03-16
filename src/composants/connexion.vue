<template>
  <div class="container-fluid h-100">
    <div class="row h-100 back">
     
      <main class="col">
      
        <div class="bienvenu">
          <h2></h2>
        </div>

        <div class="row row-cols-1 row-cols-md-3 g-4 form-con">
          <br />
           
          <form >
             <h4>Connectez vous à votre compte</h4>
            <div class=" row row-cols-1 row-cols-md-1 g-4">

            <div class="mb-3 ">
              
              login:<input
                type="text"
                class="form-control" v-model="login"
                placeholder="votre login"
              />
              
            </div>
            <div class="mb-3">
              
              mot de passe:<input
                type="password"
                class="form-control" v-model="password"
                placeholder="votre mot de passe"
              />
            </div>
            
          
            
            
            
            </div>
              
           

            
            <input type="button"  class="btn btn-primary" @click="enregistrer" value="connexion">
           
          </form>

       <!--   <gain></gain>

          <evolutiongain></evolutiongain>

          <test></test>

          <alert></alert> -->
        </div>
      </main>
    </div>
  </div>
</template>

<script>


export default {
  name: "app",
  
 
  data() {
    return {
      c: "Welcome to Your bord lateral",
      login:'',
      password:'',
      role:'',
      id:''
      
      

    };
  },
  methods: {
    enregistrer(){
      
       const login = {login: this.login, mdp:this.password };
  axios.post("http://localhost:5000/api/user/login", login)
    .then(response => {console.log(response);
      this.role= response.data.status;
      this.id= response.data.user;

    this.$emit("submit", {
        login: this.login,
        pwd: this.password,
        role: this.role,
        id:  this.id
      });
      this.$router.push('/'+this.role)

    })
    }
  }
};
</script>

<style>

</style>