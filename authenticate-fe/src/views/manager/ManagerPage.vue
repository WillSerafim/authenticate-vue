<template>
  <div class="container">
    <h1>Gerentes</h1>
    <div class="row">
      <Gerente 
      v-for="gerente in gerentes" 
      :key="gerente.numero" 
      :gerente="gerente" />
    </div>
  </div>
</template>

<script>
import Gerente from '@/components/Manager.vue'

export default {
  name: 'ManagerPage',
  components: {
    Gerente
  },
  data() {
    return {
      gerentes: [
        {
          nome: 'James',
          agencia: 1000
        },
        {
          nome: 'Pierre',
          agencia: 2000
        },
        {
          nome: 'Carlos',
          agencia: 3000
        }
      ]
    }
  }
}
</script>