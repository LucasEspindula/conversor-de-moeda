<template>
  <div id="app">
    <Header />
    <div>
      <Card :getSelectedMoeda="getSelectedMoeda" />

      <Form
        v-if="moedaSelecionada"
        :ask="askSelecionado"
        :code="codeSelecionado"
      />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Card from "./components/Card.vue";
import Form from "./components/Form.vue";

export default {
  name: "App",
  components: {
    Header,
    Card,
    Form,
  },

  data: function () {
    return {
      moedaSelecionada: null,
      askSelecionado: null,
      codeSelecionado: null,
    };
  },

  methods: {
    getSelectedMoeda: function (moedas) {
      this.moedaSelecionada = moedas;

      if (moedas.USDBRL) {
        this.askSelecionado = moedas.USDBRL.ask;
        this.codeSelecionado = moedas.USDBRL.code;
      }

      if (moedas.EURBRL) {
        this.askSelecionado = moedas.EURBRL.ask;
        this.codeSelecionado = moedas.EURBRL.code;
      }
    },
  },
};
</script>

<style>
</style>
