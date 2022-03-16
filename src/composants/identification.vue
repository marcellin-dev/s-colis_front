<template>
  <div>
    <admin v-if="user.role==='admin'" />
    <gerantagence v-else-if="user.role==='agence'" />
    <gerantbranche v-else-if="user.role==='branche'" />
    <connexion v-else @submit="login" />
  </div>
</template>

<script>

import admin from "./admin.vue";
import connexion from "./connexion.vue";
import gerantagence from './gerantagence.vue';
import gerantbranche from './gerantbranche.vue';
//import store from './loginStore'

export default {
 // store: store,
  data() {
    return {
      user: {}
      
    };
  },

  methods: {
    login({ login, pwd ,role, id}) {
      this.user = { login, pwd ,role, id};
      console.log("voici le user "+this.user.id);

      /*this.$emit("user", {
        login,
        pwd,
        role
      });*/
    }
  },
  

  components: { connexion, admin ,gerantagence, gerantbranche}
};
</script>,
   