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
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>
<template>
  <div class="form">
    <h1>Buscar Cep</h1>
    <p>Digite o cep:</p>
    <input type="text" v-model="cep" placeholder="xxxxxxxx" />
    <button @click="buscar">Buscar</button>
  </div>
  <form>
    <label for="rua">Rua</label>
    <input name="rua" type="text" v-model="endereco.logradouro" />
    <label for="bairro">Bairro</label>
    <input name="bairro" type="text" v-model="endereco.bairro" />
    <label for="localidade">Cidade</label>
    <input for="localidade" type="text" v-model="endereco.localidade" />
    <label for="estado">Estado</label>
    <input for="estado" type="text" v-model="endereco.uf" />
  </form>
</template>
<style></style>
