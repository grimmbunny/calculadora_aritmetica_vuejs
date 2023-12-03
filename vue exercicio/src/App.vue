<script setup>
import { reactive } from 'vue';

const estado = reactive({
  filtro: "",
  numero1: "",
  numero2: "",
  resultado: "",
})


function alteraNumero1(evento) {
  estado.numero1 = evento.target.value
}

function alteraNumero2(evento) {
  estado.numero2 = evento.target.value
}

function calculaSoma() {
  return Number(estado.numero1) + Number(estado.numero2)
}

function calculaSubtracao() {
  return Number(estado.numero1) - Number(estado.numero2)
}

function calculaMultiplicacao() {
  return Number(estado.numero1) * Number(estado.numero2)
}

function calculaDivisao() {
  return Number(estado.numero1) / Number(estado.numero2)
}

function calcularResultado() {
  const { filtro } = estado;

  switch (filtro) {
    case "soma":
      return calculaSoma();
    case "subtracao":
      return calculaSubtracao();
    case "multiplicacao":
      return calculaMultiplicacao();
    case "divisao":
      return calculaDivisao();
    default: 
      return "";
  }
}



</script>



<template>
    <div class="container mt-5 mx-auto text-center custom-container">
      <h1>Calculadora Aritmética VueJS</h1>
      <hr>
<form>
  <select class="form-control mt-3" v-model="estado.filtro">
    <option value="soma">Soma</option>
    <option value="subtracao">Subtração</option>
    <option value="multiplicacao">Multiplicação</option>
    <option value="divisao">Divisão</option>

  </select>

  <input type="number" placeholder="Número 1" class="form-control mt-3" @keyup="alteraNumero1" v-model="estado.numero1">
  <input type="number" placeholder="Número 2" class="form-control mt-3" @keyup="alteraNumero2" v-model="estado.numero2">



  <!-- <h2>{{ estado.numero1 }}</h2>
  <h2>{{ estado.numero2 }}</h2> -->
  <h2 class="mt-2">= {{ calcularResultado() }}</h2>




</form>

</div>
</template>



<style scoped>
.custom-container {
  max-width: 50%;
}
</style>
