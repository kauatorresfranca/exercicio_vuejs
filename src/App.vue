<script setup>
import { reactive } from 'vue';

const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};

</script>

<template>
  <div class="container">
    <h2>Calculadora Aritimétrica VueJs</h2>
    <form>
      <input @change="evento => estado.primeiroNumero = evento.target.value" type="number">
      <input @change="evento => estado.segundoNumero = evento.target.value" type="number">
      <select v-model="estado.operacaoMatematica" @change="calcularResultado">
        <option value="soma">+</option>
        <option value="subtracao">-</option>
        <option value="multiplicacao">*</option>
        <option value="divisao">/</option>
      </select>
      <span>resultado: {{ estado.resultado }}</span>
    </form>
  </div>
</template>

<style scoped>

.container{
  margin: 0 auto;
  max-width: 320px;
}

input, select{
  margin: 10px 0;
  padding: 8px;
  width: 300px;
  border: 1px solid #ccc;
  border-radius: 3px;
  display: flex;
  align-items: center;
  text-align: center;

}
</style>
