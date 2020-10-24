<template>
  <div class="container">
    <h1>Login</h1>
    <form @submit.prevent="efetuarLogin">
      <div class="form-group mb-2">
        <label for="email">E-mail</label>
        <input 
          type="text"
          class="form-control"
          v-model="usuario.email">
      </div>

      <div class="form-group mb-2">
        <label for="email">Senha</label>
        <input 
          type="text"
          class="form-control"
          v-model="usuario.senha">
      </div>

      <button 
        type="submit" 
        class="btn btn-block" style="background-color: #ff8700">
        Fazer Login
      </button>

      <router-link :to="{ name: 'novo.usuario'}">
        Não possui conta? Crie agora mesmo!
      </router-link>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      usuario: {
      }
    };
  },
  methods: {
    efetuarLogin() {
      const url = 'http://localhost:9000/auth/login';
      axios.post(url, this.usuario)
      .then(response => {
        console.log(response.data);
        localStorage.setItem('token', response.data.access_token);
        this.$router.push({ name: 'gerentes'});
      }).catch(error => {
        console.log(error);
      });
    },
  },
};
</script>

<style>
</style>