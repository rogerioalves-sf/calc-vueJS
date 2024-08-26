<script setup>
import 'bootstrap/dist/css/bootstrap.min.css';
import { reactive } from 'vue';
import {ref, computed} from 'vue';

// Declarando as variáveis reativas
const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');

// Computando o resultado
const result = computed(() => {
  switch (operation.value) {
    case '+':
      return num1.value + num2.value;
    case '-':
      return num1.value - num2.value;
    case '*':
      return num1.value * num2.value;
    case '/':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});

</script>

<template>
  <div class="container">
    <h1 class="text-center">Calculadora Aritmética</h1>
  </div>
  <div class="container-md">
    <div class="col-12">
      <form class="form-control bg-light">
        <div class="mb-3">
          <label for="num1" class="form-label">Escolha o primeiro número</label>
          <input type="number" class="form-control" id="num1" v-model.number="num1" placeholder="0">
        </div>
        <div class="mb-3">
          <label for="num2" class="form-label">Escolha o segundo número </label>
          <input type="number" class="form-control" id="num2" v-model.number="num2" placeholder="0">
          <input type="text" class="form-control mt-4" :value="result" placeholder="Resultado" readonly>
          <select class="form-control mt-4" v-model="operation">
            <option value="+">Soma</option>
            <option value="-">Subtração</option>
            <option value="*">Multiplicação</option>
            <option value="/">Divisão</option>
          </select>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
