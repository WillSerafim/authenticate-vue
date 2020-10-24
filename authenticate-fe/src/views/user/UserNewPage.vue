<template>
  <div class="container">
    <h1>Cadastro</h1>
    <form @submit.prevent="enviarFormulario">
      <div class="form group mb-2">
        <label for="name">Nome</label>
        <input 
          type="text" 
          class="form-control"
          v-model="usuario.nome"
          >
      </div>

      <div class="form group mb-2">
        <label for="email">E-mail</label>
        <input 
          type="email" 
          class="form-control"
          v-model="usuario.email"
          >
      </div>

      <div class="form group mb-2">
        <label for="password">Senha</label>
        <input
          name="password"
          type="password" 
          class="form-control"
          v-model="usuario.senha"
          >
      </div>

       <div class="form group mb-2">
        <button class="btn" type="submit" style="background-color: #ff8700">
          Salvar
        </button>
       </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'UserNewPage',
  data() {
    return {
      usuario: {
        nome: '',
        senha: '',
        email: ''
      },
    };
  },
  methods: {
    enviarFormulario() {
      const url = 'http://localhost:9000/auth/register';
      axios.post(url, this.usuario)
      .then(response => {
         console.log(response.data);
         
      }).catch(error => {
         console.log(error);
      });
    },
  },
};
</script>