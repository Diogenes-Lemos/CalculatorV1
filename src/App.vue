<script setup>
import { reactive } from 'vue';

const estado = reactive({
  valorA: 0,
  operacao: 'subtracao',
  valorB: 0,
})

function retornaResultado() {
  const operator = estado.operacao;

  switch (operator) {
    case 'adicao':
      return estado.valorA + estado.valorB;
    case 'subtracao':
      return estado.valorA - estado.valorB;
    case 'divisao':
      return estado.valorA / estado.valorB;
    case 'multiplicacao':
      return estado.valorA * estado.valorB;
  }
}
</script>

<template>
  <div class="project-area">
    <div class="calc-area">
      <div class="title-area">
        <h1>Calculadora Ligeira V1.0</h1>
      </div>
      <input class="valor" v-model.number="estado.valorA" type="number" />
      <select class="valor operator" v-model="estado.operacao" name="calc" id="calc">
        <option value="adicao">+</option>
        <option value="subtracao">-</option>
        <option value="divisao">&divide;</option>
        <option value="multiplicacao">x</option>
      </select>
      <input class="valor" v-model.number="estado.valorB" type="number" />
      <span class="valor">=</span>
      <p class="valor">{{ retornaResultado() }}</p>
    </div>
  </div>
</template>

<style scoped>
  .project-area {
    width: 100vw;
    height: 100vh;
  }

  .calc-area {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .title-area {
    display: block;
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
  }

  .valor {
    display: block;
    width: 30vw;
    height: 10vh;
    margin: 0 auto;
    font-size: 8vh;
    text-align: center;
  }

  .operator {
    width: 10vw;
  }
</style>
