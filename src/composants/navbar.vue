<template>
     <nav class="nav nav-pills nav-justified bg-ligth">
       <router-link tag="a" to="/" class="nav-link ">
      <img src="../img/logo.png"/> 
       </router-link>
    <a class="nav-link" href="#">LOGO</a>
  
    <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">LOGOUT</a>
  </nav>

</template>


<script>
export default {
    name: 'app'
}
</script>

<style>
.bg-ligth{
  background-color: rgb(255, 255, 255);
  
}
</style>