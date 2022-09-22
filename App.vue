<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },

  methods: {
    async buscar() {
      const url = `http://viacep.com.br/ws/$(this.cep)/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>
<template>
  <h1>Buscar CEP</h1>
  <form @submit.prevent="buscar">
    <input type="text" v-model="cep" placeholder="Digite o Cep" />
    <button type="submit">Buscar</button>
  </form>
  <form>
    <form class="end"></form>
    <label for="rua"></label>
    <input type="text" v-model="endereco.logradouro" />
    <label for="form"></label> <input type="text" v-model="endereco.numero" />
    <label for="bairro"></label> <input type="text" v-model="endereco.bairro" />
  </form>

  {{ endereco }}
</template>

<style>

    
</style>
