<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: 'soma',
  resultado: 0
});

const calcularResultado = () => {
  switch (estado.operacao) {
    case 'soma':
      estado.resultado = estado.numero1 + estado.numero2;
      break;
    case 'subtracao':
      estado.resultado = estado.numero1 - estado.numero2;
      break;
    case 'multiplicacao':
      estado.resultado = estado.numero1 * estado.numero2;
      break;
    case 'divisao':
      estado.resultado = estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : 'Erro: Divisão por zero';
      break;
    default:
      estado.resultado = 0;
  }
};
</script>

<template>
  <div class="container mt-5">
    <div class="card p-4">
      <h2 class="text-center mb-4">Calculadora</h2>
      <div class="row mb-3">
        <div class="col">
          <input type="number" class="form-control" placeholder="Número 1" v-model.number="estado.numero1" @input="calcularResultado">
        </div>
      </div>
      <div class="row mb-3">
        <div class="col">
          <input type="number" class="form-control" placeholder="Número 2" v-model.number="estado.numero2" @input="calcularResultado">
        </div>
      </div>
      <div class="row mb-3 d-flex justify-content-center">
        <div class="col-auto">
          <select class="form-control form-control bg-primary text-white" v-model="estado.operacao" @change="calcularResultado">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">÷</option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col text-center">
          <p class="display-4">Resultado: {{ estado.resultado }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
