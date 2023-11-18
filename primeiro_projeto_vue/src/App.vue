<script setup>
import { reactive } from 'vue';

const enderecoImagem = 'https://dfstudio-d420.kxcdn.com/wordpress/wp-content/uploads/2019/06/digital_camera_photo-1080x675.jpg';
const enderecoPintura = 'https://static.todamateria.com.br/upload/mo/na/monalisa.jpg';
const nome = 'Andrey Carlos';
const botaoEstaHabilitado = false;
const meuObjeto = {
  nome: 'Andrey',
  filmeFavorito: 'Matrix',
};

function dizOla(nome){
  return `${nome} diz oi`;
}

const gostaDeFotos = false;
const gostaDePinturas = false;

// let contador = 0;
const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferido: 0,
  nomes: ['andrey', 'carlos', 'paula'],
  nomeAInserir: ''
});

function incrementar(){
  estado.contador++;
}

function decrementar(){
  estado.contador--;
}

function alteraEmail(evento){
  evento=> estado.email = evento.target.value
}

function mostraSaldoFuturo(){
  const {saldo, transferido} = estado;
  return saldo - transferido;
}

function validaValorTransferencia(){
  const {saldo, transferido} = estado;
  return saldo >= transferido;
}

function cadastraNome(){
  const {nomeAInserir, nomes} = estado;
  nomes.push(nomeAInserir);
}
</script>

<template>
  <!-- <h1>{{ meuObjeto.filmeFavorito }}</h1>; -->
  <h1>{{ dizOla('paula') }}</h1>
  <!-- <img v-show="gostaDeFotos" :src="enderecoImagem" alt="Imagem">; -->
  <img v-if="gostaDeFotos" :src="enderecoImagem" alt="Imagem">
  <img v-else-if="gostaDePinturas" :src="enderecoPintura" alt="Imagem">
  <h2 v-else>Não curte heróis da DC</h2>

  <button :disabled="!botaoEstaHabilitado">Enviar mensagem</button>

  <br/>
  <hr/>
  
  {{ estado.contador }}
  
  <button @click="incrementar" type="button">+</button>
  <button @click="decrementar" type="button">-</button>
  
  <br/>
  <hr/>
  
  {{ estado.email }}
  
  <input type="email" @keyup="alteraEmail">
  <br/>
  <hr/>

  Saldo: {{ estado.saldo }}
  <br>
  Transferido:{{ estado.transferido }}
  <br>
  Saldo Depois da transferencia: {{ mostraSaldoFuturo() }}
  <br>
  <input :class="{ invalido: !validaValorTransferencia()}" @keyup="evento => estado.transferido = evento.target.value" type="number" placeholder="Quantia para transferir">
  <button v-if="validaValorTransferencia()"></button>
  <span v-else>Valor maior que o saldo!</span>

  <ul>
    <li v-for="nome in estado.nomes">
    {{ nome }}</li>
  </ul>
  <input @keyup="evento=> estado.nomeAInserir = evento.target.value" type="text" placeholder="Digite um novo nome">
  <button @click="cadastraNome">Cadastrar nome</button>
</template>

<style scoped>
img{
  max-width: 200px;
}

.invalido{
  outline-color: red;
  border-color: red;
}
</style>