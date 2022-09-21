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
  <body>
    <div>
      <h1>Buscar CEP</h1>
      <form @submit.prevent="buscar" class="formulario1">
        <label>CEP</label>
        <input type="text" v-model="cep" />
        <button type="submit">Buscar</button>
      </form>
      <form class="formulario2">
        <label for="rua">Rua</label>
        <input name="rua" type="text" v-model="endereco.logradouro" />
        <label for="numero">Número</label>
        <input name="numero" type="text" v-model="endereco.numero" />
        <label for="complemento">Complemento</label>
        <input name="complemento" type="text" v-model="endereco.complemento" />
        <label for="bairro">Bairro</label>
        <input name="bairro" type="text" v-model="endereco.bairro" />
        <label for="localidade">Cidade</label>
        <input name="cidade" type="text" v-model="endereco.localidade" />
        <label for="uf">Estado</label>
        <input name="estado" type="text" v-model="endereco.uf" />
      </form>
    </div>
  </body>
</template>

<style scoped>
.formulario1 {
  width: 200px;
  height: 80px;
  border: 1px solid lightgrey;
  background-color: rgba(184, 245, 224, 0.719);
  border-radius: 5px;
}
.formulario2 {
  width: 200px;
  height: 230px;
  border: 1px solid lightgray;
  background-color: rgba(184, 245, 224, 0.719);
  border-radius: 5px;
}
input {
  border: 1px solid rgb(163, 163, 163);
  align-self: center;
  border-radius: 5px;
}
button {
  border: 1px solid rgb(163, 163, 163);
  background-color: rgba(236, 253, 247, 0.918);
  width: 60px;
  height: 30px;
  margin: 10px 65px;
  border-radius: 5px;
}
body {
  display: flex;
  justify-content: center;
  background-color: rgba(211, 247, 234, 0.719);
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
</style>
