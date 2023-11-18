<script setup>
import { reactive } from 'vue';

const estado = reactive({
  valorA: 0,
  valorB: 0,
  resultado: 0,
  operacao: 'adicao',
})

const trocarFiltro = (event) => {
  estado.operacao = event.target.value;
  calcular();
}

const gravaValorA = (event) => {
  estado.valorA = event.target.value;
  calcular();
}

const gravaValorB = (event) => {
  estado.valorB = event.target.value;
  calcular();
}

const calcular = () => {
  let resultado = 0;
  let { operacao, valorA, valorB } = estado;

  switch (operacao) {
    case 'adicao':
      resultado = parseInt(valorA) + parseInt(valorB);
      break;
    case 'subtracao':
      resultado = parseInt(valorA) - parseInt(valorB);
      break;
    case 'multiplicacao':
      resultado = parseInt(valorA) * parseInt(valorB);
      break;
    case 'divisao':
      resultado = parseInt(valorA) / parseInt(valorB);
      break;
    default:
      resultado = 0;
      break;
  }
  estado.resultado = resultado;
}

</script>
<template>
  <header>
    <input @keyup="gravaValorA" type="number" placeholder="Valor A">
    <select @change="trocarFiltro">
      <option value="adicao">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">*</option>
      <option value="divisao">/</option>
    </select>
    <input @keyup="gravaValorB" type="number" placeholder="Valor B">
    <input type="text" :value="estado.resultado" disabled/>
  </header>
</template>

<style scoped>
input,
select{
  padding: 10px;
}

span{
  background-color: white;
  height: 36px;
  width: 50px;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header {
    display: flex;
    justify-content: center;
    align-items: center;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>