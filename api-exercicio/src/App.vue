<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      resultado: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>
<template>
  <h1>Buscar CEP</h1>
  <p>Digite o cep</p>
  <input type="text" v-model="cep" placeholder="xxxxxxxx" />
  <button @click="buscar">Buscar</button>
  <form>
    <label for="rua">Rua</label>
    <input name="rua" type="text" v-model="endereco.logradouro" />
  </form>
</template>
<style></style>
